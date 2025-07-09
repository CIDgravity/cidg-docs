---
title: "API integration"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
draft: false
images: []
menu:
    nextcloud:
        parent: "nextcloud-advanced-users"
        identifier: "nextcloud-advanced-users-api-integration"
weight: 203
toc: true
---

## Retrieve the path of the file

To access file or folder metadata, you need the path. The `filePath` is a path where the file is located on Nextcloud when interacting with its WebDAV server. There are 2 ways to fetch the metadata:

### Using Nextcloud WebApp

When browsing your Files, you can extract the `filePath` from the URL

{{< img src="get-filepath.png" alt="Get filePath From URI" >}}

To get the entire `filePath`, you will need to add the name of the file after the URI. In my example, the value will be

```
/PublicFilecoin/Documentation/01.jpg
```

### Using curl

When you copy, create, or move a file in Nextcloud, the `filePath` is equals to the path where you want to store the file.

```bash
curl -siu ‘<YOUR_NEXTCLOUD_USERNAME>:<YOUR_NEXTCLOUD_PASSWORD>’ \
-T <PATH_OF_LOCAL_FILE_TO_UPLOAD> \
"https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>/PublicFilecoin/"
```

In this example the `filePath` will be :

```
/PublicFilecoin/<LOCAL_FILE_NAME_TO_UPLOAD_WITH_EXTENSION>
```

## API call to get file metadata

The main information are : 
- `metadata.file.cid`
- `metadata.file.details.state`
- `metadata.file.details.retrievableCopies`

When pulling metadata from a folder, the returned information aggregates all subfolders and files within that folder. This means that querying the top-level folder provides a comprehensive view of the entire dataset, including all contained subfolders and their respective files.

Deals provide resilience by distributing file storage across multiple providers, with redundancy ensuring data availability.

### Request Format

You can track the status of a file or folder tree in real-time using the following request:

```bash
curl -X POST https://nextcloud.twinquasar.io/ocs/v2.php/apps/cidgravity/get-file-metadata \
  -u <YOUR_NEXTCLOUD_USERNAME>:<YOUR_NEXTCLOUD_PASSWORD> \
  -H "OCS-APIRequest: true" \
  -H "Content-Type: application/json" \
  -d '{"filePath": "<FILE_PATH>"}'
```

| Component                   | Description                                 |
|-----------------------------|---------------------------------------------|
| `<YOUR_NEXTCLOUD_USERNAME>` | Your Nextcloud username for authentication. |
| `<YOUR_NEXTCLOUD_PASSWORD>` | Your Nextcloud password for authentication. |
| `<FILE_PATH>`                  | The path of the uploaded file               |

### Response Format

#### Top-level Fields

| Field Name | Type    | Description                                                 |
|------------|---------|-------------------------------------------------------------|
| `success`  | boolean | Indicates if the request was successful.                    |
| `metadata` | object  | Contains the file's metadata if the request was successful. |

* * *

#### Metadata

The file details are located inside `metadata`

| Field Name     | Type   | Description                                                          |
|----------------|--------|----------------------------------------------------------------------|
| `file.cid`     | string | The CID of the file or folder used to locate it on IPFS or Filecoin. |
| `file.details` | object | Contains detailed storage and replication metadata.                  |

##### File Details

The file details are located inside `metadata.file.details`


| Field Name                   | Type    | Description                                                                           |
|------------------------------|---------|---------------------------------------------------------------------------------------|
| `state`                      | string  | Overall file storage state, e.g., one of the following values:                        |
|                              |         | \- `"Staging"` - The file is in the staging process.                                  |
|                              |         | \- `"Offloading"` - The file is in the offloading process.                            |
|                              |         | \- `"Partially offloaded"` - Only part of the file has been offloaded to Filecoin.    |
|                              |         | \- `"Offloaded"` - The entire file r folder has been offloaded to Filecoin.           |
|                              |         | \- `"Unknown"` - The file's state is unknown.                                         |
| `retrievableCopies`          | integer | Total number of retrievable copies across all groups.                                 |
| `expirationEpoch`            | integer | The Filecoin epoch when the storage agreement expires.                                |
| `expirationTimestamp`        | integer | The Filecoin epoch converted in Unix Epoch.                                           |
| `groups`                     | array   | A list of storage groups storing a portion of the file on Filecoin.                   |
| `groups[].pieceCid`          | string  | The piece CID for the stored file segment on Filecoin.                                |
| `groups[].deals`             | array   | A list of storage deals associated with this file segment.                            |
| `groups[].state`             | string  | Group's state, e.g., one of the following:                                            |
|                              |         | \- `"writable"` - The group can accept more data and will send to Filecoin when full. |
|                              |         | \- `"full"` - The group is full and ready to be pushed to Filecoin.                   |
|                              |         | \- `"VRCARDone"` - The group is ready with VRCARD completed.                          |
|                              |         | \- `"ready for deals"` - The group is ready to initiate deals.                        |
|                              |         | \- `"offloaded"` - The group has fully offloaded its contents.                        |
|                              |         | \- `"reload"` - The group is reloading for further action.                            |
| `groups[].retrievableCopies` | integer | Number of retrievable copies in this group on Filecoin.                               |

##### Deal Details

The deal details are located inside `metadata.file.details.groups[].deals`


| Field Name      | Type    | Description                                                         |
|-----------------|---------|---------------------------------------------------------------------|
| `provider`      | string  | The ID of the Filecoin provider storing the data.                   |
| `endEpoch`      | integer | The Filecoin epoch when the storage deal expires.                   |
| `dealId`        | integer | Unique Onchain verifiable identifier : https://filfox.info/en/deal/ |
| `isRetrievable` | boolean | Whether the file is currently retrievable (measured by CIDgravity). |
| `state`         | string  | State of the deal, e.g., one of the following:                      |
|                 |         | \- `"proposed"` - Deal is proposed but not yet active.              |
|                 |         | \- `"published"` - Deal has been published.                         |
|                 |         | \- `"active"` - Deal is active and ongoing.                         |

##### File states Overview

| State               | Condition                                                                                                                                                                       | Interpretation                                                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| Staging             | At least one group is still in a state that indicates it is not ready for storage operations. This could be a group in states such as `"writable"`, `"full"`, or `"VRCARDone"`. | The file is in the early stage of preparation and hasn't yet started transferring or being offloaded to storage (IPFS/Filecoin). |
| Offloading          | All groups reach at least the state `"ready for deals"`.                                                                                                                        | The file is actively in the process of being transferred or offloaded to distributed storage nodes.                              |
| Partially offloaded | All groups have at least one active storage deal.                                                                                                                               | Some groups are already offloaded or engaged with Filecoin storage deals, but the offloading is incomplete across all groups.    |
| Offloaded           | All groups have fully offloaded their data to the storage network, and no further action is required.                                                                           | The file is now completely stored and all storage deals (or copies) are confirmed.                                               |

##### Response Example

The API returns a detailed response containing file metadata.

```json
{
  "success": true,
  "metadata": {
    "file": {
      "cid": "bafybeidq6kdr4nclzhx3fdmosiivwuqoz5gtqr46564ycbxgekli7rvb2m",
      "path": "/nextcloud-1/florianruen/Documentation",
      "file": "01.jpg",
      "details": {
        "groups": [
          {
            "pieceCid": "baga6ea4seaqb2krvlu7waw267c7opqh6xb5bvjxcjwc5un764wq34jtignehygq",
            "deals": [
              {
                "provider": "f03084393",
                "endEpoch": 6599307,
                "dealId": 119988252,
                "isRetrievable": true,
                "state": "active"
              },
              {
                "provider": "f010479",
                "endEpoch": 6599308,
                "dealId": 119988665,
                "isRetrievable": true,
                "state": "active"
              },
              {
                "provider": "f0187709",
                "endEpoch": 6599308,
                "dealId": 119998759,
                "isRetrievable": false,
                "state": "active"
              },
              {
                "provider": "f02639429",
                "endEpoch": 6599308,
                "dealId": 119996721,
                "isRetrievable": true,
                "state": "active"
              },
              {
                "provider": "f020378",
                "endEpoch": 6599311,
                "dealId": 119993466,
                "isRetrievable": false,
                "state": "active"
              },
              {
                "provider": "f03134685",
                "endEpoch": 6599311,
                "dealId": 119998032,
                "isRetrievable": true,
                "state": "active"
              },
              {
                "provider": "f0717969",
                "endEpoch": 6602250,
                "dealId": 120141573,
                "isRetrievable": false,
                "state": "active"
              },
              {
                "provider": "f01249",
                "endEpoch": 6602250,
                "dealId": 120136227,
                "isRetrievable": true,
                "state": "active"
              }
            ],
            "state": "offloaded",
            "retrievableCopies": 5
          },
          {
            "state": "writable",
            "retrievableCopies": 0
          }
        ],
        "state": "staging",
        "retrievableCopies": 0
      }
    }
  }
}
```

