---
title: "Overview"
description: "Connect CIDgravity to your Nextcloud instance and start storing files on IPFS."
lead: "This documentation will guide you to configure your own Nextcloud instance with Filecoin."
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-get-started"
    identifier: "nextcloud-get-started-overview"
weight: 101
toc: true
---

## Advantages of Filecoin

### Decentralized Storage  
Filecoin operates on a decentralized network of storage providers rather than relying on a single centralized entity.

- Data is distributed across many independent nodes globally.  
- Reduces the risk of a single point of failure or data censorship.  
- Enhances resilience and data availability even if some nodes go offline.

### Verifiability  
Filecoin uses **cryptographic proofs** to ensure that data is stored correctly and remains available over time.

- Uses **Proof-of-Replication (PoRep)** and **Proof-of-Spacetime (PoSt)**.  
- Verifies data is continuously stored as promised.  
- Builds trust between users and storage providers—no need for prior relationships.  
- Enables accountability without centralized control.

### Affordable  
Filecoin creates an open, competitive marketplace for storage, making it more cost-effective.

- Prices are driven by supply and demand.  
- Users can choose providers based on cost, performance, and reputation.  
- Ideal for affordable long-term or cold data storage solutions.

To get more insight of what are the Filecoin and IPFS benefits: 
- ➡️ [What is Filecoin](https://docs.filecoin.io/basics/what-is-filecoin)
- ➡️ [What is IPFS](https://docs.ipfs.tech/concepts/what-is-ipfs)


## Architecture

{{< img src="img/architecture.png" alt="Architecture schema" >}}