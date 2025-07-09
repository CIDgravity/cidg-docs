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

At that point, you have a new folder on your user account called `Filecoin`. You can simply drop and read files are usual. All the files are automatically send and stored on Filecoin

{{< alert icon="warning" >}}
Files are stored in plain form. You must encrypt any sensitive data before uploading!
{{< /alert >}}

## File metadata

In the details panel, you’ll see IPFS-related metadata including:

* **CID**: The [Content Identifier](https://docs.ipfs.tech/concepts/content-addressing/) for the uploaded file
* **Status**: Indicates whether the file is still staged at CIDgravity or has been fully offloaded to Filecoin
* **Number of replicas from Filecoin**
* **Expiration date on the Filecoin network**

{{< alert icon="warning" >}}
Note: It may take up to 24 hours for your data to become fully available on the Filecoin network.
{{< /alert >}}

<img src="img/install_24.png" alt="CIDgravity metadata" width="640">

## Retrieve files directly on IPFS

Your data is safely replicated across the **IPFS/Filecoin network** — even if CIDgravity becomes unavailable, your content remains accessible via its **Content Identifier (CID)**.

To access your file from an public IPFS gateway:

1. Copy the **CID** from the details panel.
2. Use it with any public IPFS gateway by replacing `<CID>` in the following URL:

```
https://gateway.pinata.cloud/ipfs/<CID>
```

{{< img src="img/access-from-pinata" alt="Browse from Pinata" >}}