---
title: "Retrieval"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-retrieval"
weight: 205
toc: true
---

Access: `Retrieval` > `Deny list`

Filter retrievability over HTTP and graphsync. By applying a blacklisting or whitelisting logic to **peer IDs**.

{{< alert icon="warning" >}}
Changes are applied after clicking the "Apply" button.
{{< /alert >}}

### Blacklist / Whitelist

Select Blacklist and choose which ID or client to blacklist. Retrieval will be allowed to any other IDs.

Select Whitelist only the selected ID and clients will be able to retrieve content.

{{< img src="deny-list-blacklist.png" alt="Deny list blacklisted peer ids" >}}

When adding a new peer ID to the blacklist, you have the option to choose between one of the registered client peer IDs or input a completely new peer ID

## Booster bitswap

`booster-bitswap` is a binary that runs alongside the `boostd` process, to serve retrievals over the Bitswap protocol. 

`booster-bitswap` implements an integration with CIDgravity to retrieve settings from CIDgravity:

- **Maintenance Mode**: Provides the status of the maintenance mode, indicating whether it is active or inactive
- **Allow or Deny List**: Furnishes a list of peer IDs that are either allowed or denied within the CIDgravity deny list
- **Limits**: Presents global retrieval limits that are specifically set for the designated miner

For seamless configuration of `booster-bitswap` limits within CIDgravity and to obtain a pre-filled command, navigate to the `Settings` section. 

{{< img src="booster-bitswap-limits.png" alt="Configure the booster bitswap limits" >}}

{{< alert icon="tip" >}}
To go deeper into the documentation of booster-bitswap, you can refer to the [documentation provided on the Boost documentation](https://boost.filecoin.io/retrieving-data-from-filecoin/bitswap-retrieval)
{{< /alert >}}
