---
title: "Blacklist"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This section explain how to implement address or client blacklisting for storage deals"
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-blacklist"
weight: 103
toc: true
---

To access the blacklist section, you can navigate through the sidebar by selecting `Storage` and then `Blacklist`.

## Manage blacklisted addresses

When arriving on the page, you can find all blacklisted addresses on the right panel

{{< img src="blacklisted-addresses-list.png" alt="Manage blacklisted addresses" >}}

Each blacklisted address listed offers several options:

- **View the comment**: simply by hovering over the information icon
- **Remove**: remove this address from the blacklist, storage deals will be processed again

{{< alert icon="tip" >}}
For enhanced clarity, the address has been truncated. However, the complete address can be copied by utilizing the clipboard icon
{{< /alert >}}

{{< alert icon="tip" >}}
In the event of a multitude of addresses in the blacklist, a streamlined search functionality is available
{{< /alert >}}

## Blacklist new address

To append a new address to the blacklist, utilize the form on the left panel. 

Be careful, as the address field exclusively supports long addresses.

{{< img src="add-to-blacklist.png" alt="Add new address to blacklist" >}}

{{< alert icon="warning" >}}
Blacklisting addresses associated with registered clients is not possible. If the objective is to restrict deals from specific clients, 
the appropriate option is to block the client [via the client management page](../clients)
{{< /alert >}}
