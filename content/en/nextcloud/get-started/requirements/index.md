---
title: "Requirements"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-get-started"
    identifier: "nextcloud-get-started-requirements"
weight: 101
toc: true
---

To begin using **CIDgravity** with **Nextcloud** and store your files on **IPFS/Filecoin**, make sure you meet the following requirements.

### Set Up Your Own Nextcloud Instance (only you use it as relay)

CIDgravity is designed to be added to your personal or organization-managed Nextcloud instance.

You can install Nextcloud using various methods:

* On a Linux server (manual or scripted)
* With Docker (ideal for quick testing)
* Via Snap, VM images, or cloud providers

📖 **Official Installation Guide**:
👉 [https://nextcloud.com/install/](https://nextcloud.com/install/)

### What Is a CID (Content Identifier)?

A **CID**, or Content Identifier, is a cryptographic hash that uniquely represents a piece of content in decentralized storage systems like **IPFS** and **Filecoin**.

It acts as a permanent, tamper-proof fingerprint of the file, enabling secure retrieval from any peer on the network.

#### Key Concepts:

* **Content Addressing**
  A CID points directly to content, not a location. If a file exists on the network, it can be retrieved using its CID.

* **Immutability**
  Any change to the content changes the CID, guaranteeing integrity and preventing unnoticed tampering.

* **Use in IPFS & Filecoin**
  These networks rely on CIDs for storage and access. CIDgravity uses this system to store and reference your files.

📚 Learn more about content addressing:
👉 [https://docs.ipfs.tech/concepts/content-addressing/](https://docs.ipfs.tech/concepts/content-addressing/)


{{< alert icon="warning" >}}
Only files placed inside the `/Public Filecoin` directory are actually stored on **Filecoin** via CIDgravity.
Any files stored **outside** this directory will remain on **Twin Quasar's internal file servers** and **not** be replicated on the decentralized network.
{{< /alert >}}