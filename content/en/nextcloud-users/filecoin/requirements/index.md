---
title: "Requirements"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide describes how you start using Nextcloud to onboard data to Filecoin."
draft: false
images: []
menu:
    nextcloud-users:
        parent: "nextcloud-users-filecoin"
        identifier: "nextcloud-users-filecoin-requirements"
weight: 200
toc: true
---

Use Nextcloud as a Gateway to Filecoin

Welcome to the **Nextcloud as a Gateway to Filecoin Documentation**. This guide provides a structured, comprehensive walkthrough for setting up, configuring, and utilizing Nextcloud with Filecoin. It includes **file offloading**, **metadata access**, and **data retrieval** from Filecoin with examples for **NodeJS, Go, Python, and Rclone**.

This documentation corresponds to the "Starter" Offer. To unlock advanced features such as:

- Using your own Filecoin address
- Custom onboarding strategy
- Advanced onboarding dashboards

You will need a dedicated gateway and subscribe at least to the Pro Tier. For more information on these advanced features and pricing, visit [CIDgravity Pricing](https://www.cidgravity.com/pricing).

Before starting, ensure the following prerequisites are met:

1. **Create an account on :** https://nextcloud.twinquasar.io
2. **Obtain the WebDAV URL for Your Account:**
    The WebDAV URL allows you to connect any apps to the Nextcloud instance.
    
    - Example URL format:

```
https://nextcloud.twinquasar.io/remote.php/dav/files/<username>/
```

{{< video src="get-webdav-url.mp4" attributes="controls" width="960" >}}




</br>
</br>
</br>

3. **Understanding what is a CID (Content Identifier)** :

A CID is a unique identifier used in decentralized storage systems like IPFS (InterPlanetary File System) or Filecoin to reference and locate specific pieces of content. CIDs are cryptographic hashes derived from the content itself, ensuring data integrity and uniqueness. They are essential in decentralized storage because they eliminate the need for a central index or server by allowing users to directly access content based on its hash.

**Key Points About CIDs**

- **Content Addressing:** CIDs allow direct content access based on the content's unique hash rather than its location. This means that if you know the CID, you can fetch the data from any node that hosts it.
- **Immutable:** Because the CID is derived from the content's hash, the content itself cannot be altered without changing its CID.
- **Use in IPFS/Filecoin:** In decentralized networks like IPFS or Filecoin, CIDs are used to store and share files. The CID serves as a pointer to a stored file or segment of data, enabling retrieval.


More infos : [https://docs.ipfs.tech/concepts/content-addressing/](https://docs.ipfs.tech/concepts/content-addressing/)

4.  **Important:**
    Only files in `/Public Filecoin` are stored on Filecoin.
    Files outside this directory are stored on Twin Quasar's file servers.
