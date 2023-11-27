---
title: "Clients"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "Group address, apply custom pricing and acceptance criterias, give priority, and get advanced insight on clients activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-clients"
weight: 200
toc: true
---

Client is a core component of CIDgravity.

Access: `Storage` > `Client`

## Create new client

Clients can be created from the client page or by clicking on any client proposed name from `dashboards` or `history`.

### Pricing model and acceptance logic

When creating a client you can select to apply a specific pricing and acceptance logic to that client.
It's fine to not selecting one, the default pricing and/or acceptance logic will then apply.

{{< alert icon="warning" >}}
When relying on the default pricing / acceptance logic. Any modifications or changes on the default settings, will automatically apply to that client too.
{{< /alert >}}

### Client identity

{{< img src="identity-infos.png" alt="Fill the identity information about the client" >}}

### Filecoin addresses

Fill all Filecoin addresses used by the client. 

There are no constraints on the number of addresses that can be linked to a client.

After an address is entered press ENTER to start the address validation. 

{{< alert icon="tip" >}}
Both short and long Filecoin address format are supported. 
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

It's possible to specify client specific limits, keep in mind this is an additional limit, it does not override the global limits. More information on [limits]({{< ref "storage-providers/manage/others/index.md#limits" >}}).

{{< alert icon="tip" >}}
To disable client specific limits, set it to 0.
{{< /alert >}}

{{< img src="storage-limits.png" alt="Manage storage deal rate for this client" >}}

### Start epoch sealing buffer

This setting overrides the global start epoch sealing buffer.
More information on the [start epoch sealing buffer]({{< ref "storage-providers/manage/others/index.md#start-epoch-sealing-buffer" >}}).

{{< alert icon="warning" >}}
The value must be express in hours
{{< /alert >}}

{{< img src="start-epoch-sealing-buffer.png" alt="Define a value for the start epoch sealing buffer" >}}

## Block a client

When enabled, this feature start rejecting all deals from a specific client. 

A custom message is concatenated to the rejection message sent back to the client.
