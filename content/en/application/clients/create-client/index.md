---
title: "Create new client"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
lead: "This guide describes how you can create a new client in CIDgravity"
draft: false
images: []
menu:
    application:
        parent: "application-clients"
        identifier: "application-clients-create"
weight: 101
toc: true
---

You can navigate in the sidebar under `Clients`

On the top, you can click on `Create a new client`

### 1. Select a pricing model

The first thing you need to do to create a customer is to choose the pricing model you want to apply to it

This information is mandatory, even if you want to apply the default pricing model to it.

### 2. Fill the identity information

When the pricing model is selected, the first block asks you to provide information to identify your customer

![Fill the identity information about the client](identity-infos.png)

### 3. Manage Filecoin addresses

To identify the customer when new storage deals arrive, you must enter all the Filecoin addresses known to him

{{< alert icon="tip" >}}
You can enter the short address (ID address) or the long address. Each time you press enter, we will show you the one you did not enter for verification
{{< /alert >}}

{{< alert icon="tip" >}}
There is no limitation on the number of addresses that can be associated with a client
{{< /alert >}}

![Manage Filecoin addresses for this client](filecoin-addresses.png)

### 4. Manage client Peer IDs

To identify the customer when new retrieval deals arrive, you must enter all the Peer IDS known to him

{{< alert icon="warning" >}}
For Peer IDs, only long format is supported (12D format [...])
{{< /alert >}}

{{< alert icon="tip" >}}
There is no limitation on the number of Peer IDs that can be associated with a client
{{< /alert >}}

![Manage client Peer IDs](client-peer-ids.png)

### 5. Storage deal rate

Independently of the global clients defined for the miner, it is possible to define clients specific to this client. Once exceeded, all of its deals will be rejected until reset.

{{< alert icon="tip" >}}
To set no limits, simply leave both fields at 0
{{< /alert >}}

![Manage storage deal rate for this client](storage-limits.png)

### 6. Start epoch sealing buffer

This parameter, specific to this client, allows you to define a minimum duration for sealing a sector. 
All deals from this client below this minimum duration will be rejected

By default, the miner's global values apply, but you can define one that will only apply to this client

{{< alert icon="warning" >}}
This value must be expressed in hours
{{< /alert >}}

![Define a value for the start epoch sealing buffer](start-epoch-sealing-buffer.png)

