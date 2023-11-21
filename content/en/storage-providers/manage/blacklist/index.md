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
weight: 203
toc: true
---

Access `Storage` > `Blacklist`.

When an address is blacklisted any deals form that address are automatically deleted without being evaluated. The client is informed by an unauthorized message.

## Blacklist new address

To append a new address to the blacklist, use the form on the left panel. 

{{< alert icon="tip" >}}
The address field exclusively supports long format addresses.
{{< /alert >}}

{{< img src="add-to-blacklist.png" alt="Add new address to blacklist" >}}

{{< alert icon="warning" >}}
Blacklisting addresses associated with registered clients is not possible. If you want to restrict deals from a specific client, 
the appropriate option is to block the client from the `Client` page
{{< /alert >}}

## Manage blacklisted addresses

{{< img src="blacklisted-addresses-list.png" alt="Manage blacklisted addresses" >}}

- **View the comment**: simply by hovering over the information icon
- **Remove**: remove this address from the blacklist, storage deals will be processed again

