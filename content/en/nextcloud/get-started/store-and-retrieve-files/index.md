---
title: "Store and retrieve files"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-get-started"
    identifier: "nextcloud-get-started-store-and-retrieve-files"
weight: 105
toc: true
---

At that point, you have a new folder on your user account called `IPFS Vault`. You can simply drop and read files are usual. All the files are automatically send and stored on Filecoin

{{< alert icon="warning" >}}
The files are stored as is on Filecoin. You need to encrypt any sensitive data!
{{< /alert >}}

## Open file details
Once your file is uploaded, click the **three dots (⋯)** next to the file name and select **Open details**. 

This will open a sidebar with additional metadata. 

<img src="img/install_23.png" alt="Open file details" width="640">
<br /><br />

### Retrieve files directly on IPFS

Your data is safely replicated across the **IPFS/Filecoin network** — even if CIDgravity becomes unavailable, your content remains accessible via its **Content Identifier (CID)**.

To access your file from an public IPFS gateway:

1. Copy the **CID** from the file details panel.
2. Use it with any public IPFS gateway by replacing `<CID>` in the following URL:

```
https://gateway.pinata.cloud/ipfs/<CID>
```

{{< img src="img/access-from-pinata" alt="Browse from Pinata" >}}


## Access file metadata

In the details panel, you’ll see IPFS-related metadata including:

* **CID**: The Content Identifier for the uploaded file
* **Status**: Whether the file is uploaded, pinned, or in progress
* **Replication progress**: Tracks how many IPFS/Filecoin replicas exist

{{< alert icon="warning" >}}
Note: It may take up to 24 hours for your data to become fully available on the Filecoin network.
{{< /alert >}}

This confirms your file has been successfully added to the IPFS network. 

<img src="img/install_24.png" alt="CIDgravity metadata" width="640">
