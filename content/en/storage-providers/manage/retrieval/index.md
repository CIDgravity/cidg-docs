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

## Deny list

Similar to the blacklist feature for storage, you can apply blacklisting or whitelisting to peer IDs for retrieval deals. 

Access this functionality by navigating to the `Retrieval` section and selecting `Deny list`.

To enable this feature, you must choose the desired behavior between `Blacklist` and `Whitelist`. 
This customization allows you to precisely control the peer IDs permitted or prohibited in retrieval deals.

{{< alert icon="warning" >}}
The applied changes are not reflected in realtime; to ensure the modifications take effect, it is necessary to click on the "Apply" button
{{< /alert >}}

### Blacklist

To utilize the Blacklist behavior, simply click on the radio button next to the `Blacklist` title. 
This action sets the mode to blacklist, enabling you to restrict specific peer IDs.

To add blacklisted peer IDs, click on the `+` button located under the table. 

{{< img src="deny-list-blacklist.png" alt="Deny list blacklisted peer ids" >}}

When adding a new peer ID to the blacklist, you have the option to choose between one of the registered client peer IDs or input a completely new peer ID

### Whitelist

To utilize the Whitelist behavior, simply click on the radio button next to the `Whitelist` title. 
This action sets the mode to whitelist, enabling you to allow specific peer IDs.

To add whitelisted peer IDs, click on the `+` button located under the table. 

{{< img src="deny-list-whitelist.png" alt="Deny list whitelisted peer ids" >}}

When adding a new peer ID to the whitelist, you have the option to choose between one of the registered client peer IDs or input a completely new peer ID

## Booster bitswap

`booster-bitswap` is a binary that runs alongside the `boostd` process, to serve retrievals over the Bitswap protocol. 

This feature of boost provides a number of tools for managing a production grade Bitswap retrieval service for a Storage Provider's content.

When using CIDgravity, the `booster-bitswap` functionality can be configured to retrieve pertinent information associated with the miner. This includes:

- **Maintenance Mode**: Provides the status of the maintenance mode, indicating whether it is active or inactive
- **Allow or Deny List**: Furnishes a list of peer IDs that are either allowed or denied within the CIDgravity deny list
- **Limits**: Presents global retrieval limits that are specifically set for the designated miner

For seamless configuration of `booster-bitswap` limits within CIDgravity and to obtain a pre-filled command, navigate to the `Settings` section. 

{{< img src="booster-bitswap-limits.png" alt="Configure the booster bitswap limits" >}}

{{< alert icon="tip" >}}
To go deeper into the documentation of booster-bitswap, you can refer to the [documentation provided on the Boost documentation](https://boost.filecoin.io/retrieving-data-from-filecoin/bitswap-retrieval)
{{< /alert >}}
