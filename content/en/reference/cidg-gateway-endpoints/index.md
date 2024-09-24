---
title: "CIDgravity Gateway Endpoints"
description: "This section contains reference information for the CIDgravity gateway endpoints. These endpoints are only accessible when running a CIDgravity gateway."
draft: false
images: []
menu:
    reference:
        parent: "reference-cidg-gateway-endpoints"
        identifier: "reference-cidg-gateway-endpoints-list"
weight: 100
toc: true
---

The File Information API provides essential details about files onboarded to the Filecoin network via the CIDgravity Gateway. This API is intended exclusively for clients using the CIDgravity Gateway to store files on Filecoin.

Note: These API endpoints require access to the CIDgravity Gateway for communication. Without this access, the API cannot be used.

## Endpoints description

<details open>
 <summary><code>POST</code> <code><b>/file-info</b></code> <code>(Get element metadata)</code></summary>

This endpoint allows you to retrieve the current status and details of files or folders that have been uploaded to the CIDgravity Gateway for onboarding to Filecoin. This API supports both individual files and folders, providing relevant information about their storage state and retrievability.

###  File vs. Folder Handling
- **Files**: When querying a file, the returned state and details apply only to that specific file.
  
- **Folders**: When querying a folder, the API returns a state representing the folder as a whole, which is an aggregated view of the states of all its sub-elements (i.e., files and subfolders within it).

This distinction is important because a folder can contain multiple files, each with its own storage state and deal status. The folder's overall state is a combined representation of the status of its contents, providing a single, comprehensive view of the entire folder's state on Filecoin.

### Parameters
> | **Name**  | **Type**  | **Description**                                                                                       |
> |----------------|-----------|-------------------------------------------------------------------------------------------------------|
> | `filePath`     | required `string`  | The path to the file or folder to be queried.                                                          |
> | `verbose`      | optional `boolean` | Specifies the level of detail in the response. Defaults to `false`.                                    |
> |                |           | - `False`: Returns basic information such as the CID of the element.                                   |
> |                |           | - `True`: Returns detailed information including the file’s state, retrievable copies, and deal data.   |

### Responses
> | **Field**                    | **Type**    | **Description**                                                                                         |
> |------------------------------|-------------|---------------------------------------------------------------------------------------------------------|
> | `success`                    | `boolean`   | Indicates whether the request was successful (`true` or `false`).                                        |
> | `error`                      | `string`    | Error message provided if `success` is `false`.                                                         |
> | `result`                     | `object`    | Contains details of the file or folder if `success` is `true`.                                           |
> | `result.file`                | `object`    | Contains the file’s basic or detailed information.                                                       |
> | `result.file.cid`            | `string`    | The file's unique CID (Content Identifier) for retrieval on IPFS.                                        |
> | `result.file.details`        | `object`    | (Optional) Additional file details, returned if `verbose: true`.                                         |
> | `result.file.details.state`              | `string`    | Current state of the file (See **File States** below).                                                |
> | `result.file.details.retrievableCopies`  | `int`       | Minimum number of retrievable copies across all groups.|
> | `result.file.details.groups[]`             | `array`     | Information about the groups associated with the file or folder.|
> | `result.file.details.groups[].state`               | `string`    | The state of the group (See **Group States** below).|
> | `result.file.details.groups[].pieceCid`            | `string`    | Block Piece CID if available.|
> | `result.file.details.groups[].retrievableCopies`   | `int`       | Number of retrievable copies available within the group.|
> | `result.file.details.groups[].deals[]`               | `array`     | (Optional) List of active deals, returned only if the group is in a sufficient state to have deals.       |
> | `result.file.details.groups[].deals[].provider`      | `string`    | The provider offering the deal.|
> | `result.file.details.groups[].deals[].state`         | `string`    | The state of the deal (See **Deal States** below).|
> | `result.file.details.groups[].deals[].dealId`        | `int`       | The unique ID of the deal.                                                                   |
> | `result.file.details.groups[].deals[].endEpoch`      | `int`       | The epoch at which the deal ends.                                                  |
> | `result.file.details.groups[].deals[].isRetrievable` | `boolean`   | Indicates whether the file is retrievable through this deal.          |

### States
#### File States
> | **State**              | **Description**                                                                                           |
> |------------------------|-----------------------------------------------------------------------------------------------------------|
> | `staging`              | At least one group is not yet fully ready (either `writable`, `full`, or `VRCARDone`).                    |
> | `offloading`           | All groups are ready, and the file is being offloaded to Filecoin.                                         |
> | `partially_offloaded`  | All groups have at least one active deal.                                                                 |
> | `offloaded`            | All groups are offloaded, and the file is fully stored.                                                   |

#### Group States
> | **State**              | **Description**                                                                                           |
> |------------------------|-----------------------------------------------------------------------------------------------------------|
> | `writable`             | The group is writable and accepting data.                                                                 |
> | `full`                 | The group is full and ready for further processing.                                                       |
> | `VRCARDone`            | The CAR file for the group is generated.                                                                  |
> | `ready_for_deals`      | The group is ready to engage in storage deals on Filecoin.                                                |
> | `offloaded`            | The group has been offloaded to Filecoin and removed from the CIDgravity Gateway.                         |
> | `reload`               | The group is in the process of being reloaded onto the system.                                            |

#### Deal States
> | **State**      | **Description**                                                                                                   |
> |----------------|-------------------------------------------------------------------------------------------------------------------|
> | `proposed`     | The deal has been proposed, awaiting further steps.                                                               |
> | `published`    | The deal has been published and is visible on the Filecoin network.                                                |
> | `active`       | The deal is active and the file is being stored as per the terms of the deal.   

### Example cURL
> ```bash
> $ curl -s -X POST http://localhost:9011/file-info -d '{"filePath": "/myfile"}' | jq .
> ```

#### Response (Success):
> ```json
> {
>   "success": true,
>   "result": {
>     "file": {
>       "cid": "QmUNLLsPACCz1vLxQVkXqqLX5R1X345qqfHbsf67hvA3Nn"
>     }
>   }
> }
> ```

#### Response (Error):
> ```json
> {
>   "success": false,
>   "error": "File not found"
> }
> ```
</details>

