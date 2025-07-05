---
title: "Accessing Data"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
draft: false
images: []
menu:
    nextcloud:
        parent: "nextcloud-advanced-users"
        identifier: "nextcloud-advanced-users-accessing-data"
weight: 104
toc: true
---

As soon as a group is offloaded, the data is deleted from the gateway and only stored on Filecoin.

### With Nextcloud

Nextcloud can act as a gateway to Filecoin by allowing authenticated and mapped access to the `/Public Filecoin/` directory.
You can transparently browse the files through Nextcloud. Nextcloud retrieves the files from Filecoin on your behalf.

Using our Nextcloud instance provides high bandwidth and low latency leveraging features, like **Sharding** or **Bandwidth Aggregation**. 
However, you can also leverage any public IPFS gateway or set up your own IPFS node to gain direct access to the data.

### With Public IPFS Gateways

Any file with `retrievableCopies >= 1` can be browsed via public IPFS gateways. Simply replace `<CID>` with your file's CID.

#### Example Public Gateway URL:

```
https://gateway.pinata.cloud/ipfs/<CID>
```

{{< img src="access-from-piniata" alt="Browse from Pinata" >}}

### With Kubo Desktop

Any file with `retrievableCopies >= 1` can be accessed using public IPFS gateways. Simply replace `<CID>` with your file's CID.

Kubo Desktop provides an intuitive interface for accessing IPFS data.

#### Steps:

1. Open Kubo Desktop.
2. Use the CID to fetch your file directly

{{< video src="access-from-kubo.mp4" attributes="controls" width="960" >}}
