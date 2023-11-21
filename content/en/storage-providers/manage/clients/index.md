---
title: "Clients"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide describes how you can manage clients"
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-clients"
weight: 200
toc: true
---

## Manage existing clients

You can access the navigation menu within the sidebar under the `Clients` section.

{{< img src="clients-list.png" alt="Manage clients using the client management page" >}}

On this page, you have real-time access to the miner's global limits for both storage and retrieval.

For each customer listed, various options are available:

- **Edit**: You can modify all the information associated with a specific client
- **Delete**: This option allows you to remove a client from the list
- **Block / Release a client**: You can use this feature to either reject all deals originating from a particular client or allow them. This action also permits you to specify a - customized rejection message, which will be communicated to the client in case of deal rejection

## Create new client

At the top of the page, you'll find the option to initiate the creation of a new client by simply clicking on `Create a new client`

#### 1. Select a pricing model and storage acceptance logic

The initial step in client creation necessitates the selection of the pricing model and a storage acceptance logic to be associated with them. 

{{< alert icon="warning" >}}
For both the pricing model and acceptance logic, in the absence of user-defined configurations, the system will automatically apply the default settings. 

Consequently, any modifications to the default settings will directly influence the behavior of proposals originating from these clients.
{{< /alert >}}

#### 2. Fill the identity information

Once the pricing model has been selected, the initial section prompts you to furnish client identification details.

{{< img src="identity-infos.png" alt="Fill the identity information about the client" >}}

#### 3. Manage Filecoin addresses

For the purpose of customer identification when new storage deals are initiated, it is imperative to input all the Filecoin addresses associated with the client.

{{< alert icon="tip" >}}
You have the option to input either the short address (ID address) or the long address. Upon each entry, we will display the one you didn't enter for verification.
{{< /alert >}}

{{< alert icon="tip" >}}
There are no constraints on the quantity of addresses that can be linked to a client.
{{< /alert >}}

{{< img src="filecoin-addresses.png" alt="Manage Filecoin addresses for this client" >}}

#### 4. Manage client Peer IDs

In order to identify the customer when new retrieval deals are received, it is imperative to provide all the known Peer IDS associated with the client

{{< alert icon="warning" >}}
Please note that for Peer IDs, exclusively the long format (12D format) is supported.
{{< /alert >}}

{{< alert icon="tip" >}}
There are no constraints on the quantity of Peer IDs that can be linked to a client.
{{< /alert >}}

{{< img src="client-peer-ids.png" alt="Manage client Peer IDs" >}}

#### 5. Set rate limits

Irrespective of the global limits for the miner, it is feasible to establish limits only to this specific client. 

Once their limits are reached, all of the customer's deals will be rejected until a reset is performed.

{{< alert icon="tip" >}}
For no limits, simply leave both fields set at 0
{{< /alert >}}

{{< img src="storage-limits.png" alt="Manage storage deal rate for this client" >}}

#### 6. Start epoch sealing buffer

You can set a specific start epoch sealing buffer for this specific client.
Any deals from this client with a start epoch below this specified minimum will be rejected. 

By default, if nothing is set for the client, the miner global values will be used.

{{< alert icon="warning" >}}
The value must be express in hours
{{< /alert >}}

{{< img src="start-epoch-sealing-buffer.png" alt="Define a value for the start epoch sealing buffer" >}}
