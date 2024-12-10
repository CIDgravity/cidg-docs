---
title: "Get metadata"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "File Metadata contains, all information related to files or folders state on Filecoin and retrievability."
draft: false
images: []
menu:
    nextcloud-users:
        parent: "nextcloud-users-filecoin"
        identifier: "nextcloud-users-filecoin-get-metadata"
weight: 203
toc: true
---

### Requirement

To access file or folder metadata, you need the `fileId`. The `fileId` is a unique identifier provided by Nextcloud when interacting with its WebDAV server. There are 3 ways to fetch the metadata:

#### Option 1: Nextcloud WebApp

When browsing your Files, you can extract the fileId from the URL

{{< img src="get-fileid.png" alt="Get fileId From URI" >}}

#### Option 2: Fetching File Metadata Using HTTP Headers

When you copy, create, or move a file in Nextcloud, the `OC-FileId` is sent in the response headers.

##### Example:

```bash
curl -siu ‘<YOUR_NEXTCLOUD_USERNAME>:<YOUR_NEXTCLOUD_PASSWORD>’ \
-T <PATH_OF_LOCAL_FILE_TO_UPLOAD> \
"https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>/Public%20Filecoin/"
```

The headers returned will include something like:

```
OC-FileId: 1234567890
```

#### Option 3: Fetching File Metadata Using a WebDAV `PROPFIND` Query

You can make a WebDAV query with a curl request to fetch the fileId.

##### Example Curl Command:

```bash
curl -su '<YOUR_NEXTCLOUD_USERNAME>:<YOUR_NEXTCLOUD_PASSWORD>’ \
-X PROPFIND \
-H "Depth: 0" \
-d '<?xml version="1.0"?><d:propfind xmlns:d="DAV:" xmlns:oc="http://owncloud.org/ns"><d:prop><oc:fileid/></d:prop></d:propfind>' \
"https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>/Public%20Filecoin/<FILE_PATH>“
```

The response contains the fileId “oc:fileid”

**Hint : you can use the command xmllint to extract that value**

```
xmllint --xpath "//*[local-name()='fileid']/text()" -
```

### get-file-metadata API call


The main information are : 
- file.cid
- file.details.state
- file.details.retrievableCopies

When pulling metadata from a folder, the returned information aggregates all subfolders and files within that folder. This means that querying the top-level folder provides a comprehensive view of the entire dataset, including all contained subfolders and their respective files.

Deals provide resilience by distributing file storage across multiple providers, with redundancy ensuring data availability.

### Request Format

You can track the status of a file or folder tree in real-time using the following request:

```bash
curl -u '<YOUR_NEXTCLOUD_USERNAME>:<YOUR_NEXTCLOUD_PASSWORD>' \
-X GET "https://nextcloud.twinquasar.io/ocs/v2.php/apps/cidgravity_gateway/get-file-metadata?fileId=<FILE_ID>"
```

| Component                   | Description                                 |
|-----------------------------|---------------------------------------------|
| `<YOUR_NEXTCLOUD_USERNAME>` | Your Nextcloud username for authentication. |
| `<YOUR_NEXTCLOUD_PASSWORD>` | Your Nextcloud password for authentication. |
| `fileId`                    | The unique identifier of the file           |

### Response Format

### Top-level Fields

| Field Name | Type    | Description                                                 |
|------------|---------|-------------------------------------------------------------|
| `success`  | boolean | Indicates if the request was successful.                    |
| `metadata` | object  | Contains the file's metadata if the request was successful. |

* * *

### Metadata -  (Inside `metadata`)

| Field Name     | Type   | Description                                                          |
|----------------|--------|----------------------------------------------------------------------|
| `file.cid`     | string | The CID of the file or folder used to locate it on IPFS or Filecoin. |
| `file.details` | object | Contains detailed storage and replication metadata.                  |

* * *

### File Details - (Inside `metadata.file.details`)

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

* * *

### Deal Details (Inside `metadata.file.details.groups[].deals`)

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

### File states Overview
| State               | Condition                                                                                                                                                                       | Interpretation                                                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| Staging             | At least one group is still in a state that indicates it is not ready for storage operations. This could be a group in states such as `"writable"`, `"full"`, or `"VRCARDone"`. | The file is in the early stage of preparation and hasn't yet started transferring or being offloaded to storage (IPFS/Filecoin). |
| Offloading          | All groups reach at least the state `"ready for deals"`.                                                                                                                        | The file is actively in the process of being transferred or offloaded to distributed storage nodes.                              |
| Partially offloaded | All groups have at least one active storage deal.                                                                                                                               | Some groups are already offloaded or engaged with Filecoin storage deals, but the offloading is incomplete across all groups.    |
| Offloaded           | All groups have fully offloaded their data to the storage network, and no further action is required.                                                                           | The file is now completely stored and all storage deals (or copies) are confirmed.                                               |

#### Response Example

The API returns a detailed response containing file metadata.

```json
{
  "success": true,
  "metadata": {
    "file": {
      "cid": "QmYLX2WS5Yb2SsUe8iL53osM9Wgx5xFpTrtr4QiN5nouxH",
      "details": {
        "groups": [
          {
            "pieceCid": "baga6ea4seaqlne54hvmeopx2yh335nay2oyae4crwpqqyosscwdz5tw7lix32pa",
            "deals": [
              {
                "provider": "f010479",
                "endEpoch": 5968776,
                "dealId": 97326078,
                "isRetrievable": true,
                "state": "active"
              },
              {
                "provider": "f0717969",
                "endEpoch": 5968776,
                "dealId": 97529013,
                "isRetrievable": true,
                "state": "active"
              }
            ],
            "state": "offloaded",
            "retrievableCopies": 8
          }
        ],
        "state": "offloaded",
        "retrievableCopies": 8,
        "expirationEpoch": 5971777,
        "expirationTimestamp": 1777459710
      }
    }
  }
}
```

