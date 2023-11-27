---
title: "Clients"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "Group address under a client, apply custom pricing, specific acceptance criterias, priority, and get advanced insight on clients activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-clients"
weight: 200
toc: true
---


Access: `Storage` > `Client`

## Create new client

Clients can be created from the client page or by clicking on any client name proposition from `dashboards` or `history`.

### Pricing model and acceptance logic

When creating a client you can select to apply a specific pricing and acceptance logic to that client.
It's fine to not selecting one, the default pricing and/or the default acceptance logic will apply.

{{< alert icon="warning" >}}
When relying on the default pricing/acceptance logic. Any modification or change on the default settings, will automatically apply to that client too.
{{< /alert >}}

### Client identity

{{< img src="identity-infos.png" alt="Fill the identity information about the client" >}}

### Filecoin addresses

Fill any Filecoin addresses used by the client. 

There are no constraints on the quantity of addresses that can be linked to a client.

After an address is entered press ENTER to start the address validation. 

{{< alert icon="tip" >}}
Both short and long format are supported. 
{{< /alert >}}

{{< img src="filecoin-addresses.png" alt="Manage Filecoin addresses for this client" >}}

### Peer IDs

In order to identify the customer when new retrieval deals are received, it is imperative to provide all the known Peer IDS associated to the client.

{{< alert icon="warning" >}}
Please note that for Peer IDs, exclusively the long format (12D format) is supported.
{{< /alert >}}

{{< alert icon="tip" >}}
There are no constraints on the quantity of Peer IDs that can be linked to a client.
{{< /alert >}}

{{< img src="client-peer-ids.png" alt="Manage client Peer IDs" >}}

### Rate limits

It's possible to specify client specific limits, keep in mind this is an additional limit to a client, it does not override the global limits. More information on [limits]({{< ref "storage-providers/manage/others#global-limits" >}})

{{< alert icon="tip" >}}
To disable client specific limits, set it to 0.
{{< /alert >}}

{{< img src="storage-limits.png" alt="Manage storage deal rate for this client" >}}

### Start epoch sealing buffer

You can set a specific start epoch sealing buffer per client.
Any deals from this client with a start epoch below this specified minimum will be rejected. 

By default, if nothing is set for the client, the miner global values will be used.

[start epoch sealing buffer]({{< ref "storage-providers/manage/others#start-epoch-sealing-buffer" >}})

{{< alert icon="warning" >}}
The value must be express in hours
{{< /alert >}}

{{< img src="start-epoch-sealing-buffer.png" alt="Define a value for the start epoch sealing buffer" >}}

## Manage existing clients

You can access the navigation menu within the sidebar under the `Clients` section.

{{< img src="clients-list.png" alt="Manage clients using the client management page" >}}

On this page, you have real-time access to the miner's global limits for both storage and retrieval.

For each customer listed, various options are available:

- **Edit**: You can modify all the information associated with a specific client
- **Delete**: This option allows you to remove a client from the list
- **Block / Release a client**: You can use this feature to either reject all deals originating from a particular client or allow them. This action also permits you to specify a - customized rejection message, which will be communicated to the client in case of deal rejection

