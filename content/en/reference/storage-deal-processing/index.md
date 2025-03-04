---
title: "Storage deal processing"
description: "This section explain how the incoming deals are processed by CIDgravity using clients, pricing, limits and acceptance logic"
draft: false
images: []
menu:
    reference:
        parent: "reference-storage-deal-processing"
        identifier: "reference-storage-deal-processing-overview"
weight: 101
toc: true
---

Deals processing is a core component of CIDgravity, most of the features in CIDgravity will impact the acceptance of a deal. Through this article you will understand how all these components will work together to get the best out CIDgravity.

The decision outcome is binary:

- `Accept`: The proposal successfully meets all criteria, allowing for processing by Curio,Boost/Venus.
- `Reject`: The proposal fails to satisfy one or more criteria, leading to rejection. The rejection reason is explicitly specified in the deal filter response.

## How does it works ?

When a deal is received and passed by Curio,Boost/Venus to CIDgravity, it follows the workflow below :

{{< img src="storage-deal-flow.png" alt="Storage deal flow in CIDgravity" >}}

- **Proposal integrity**: verify the integrity of the incoming proposal 
	- integrity checks
	- format
	- value threshold
	- etc...
- **Client identification and authorization**: identify the client associated with the incoming deal and grant authorization based on :
	- Deal acceptance from unknown clients
	- Client is blocked ([doc]({{< ref "storage-providers/manage/clients/index.md#manage-existing-clients" >}}) )
	- Blacklist ([doc]({{< ref "storage-providers/manage/blacklist/index.md" >}}) )

- **Pricing model**: confirm the pricing is in line with the client pricing model :
	- Default pricing model for unknown clients
	- Client pricing model when the client is identified
	- Client pricing model followed by the default pricing model if the "Fallback to default pricing model is set on the client pricing model
- **Maintenance mode**: evaluate whether the miner is currently in maintenance mode ([doc]({{< ref "storage-providers/manage/others/index.md#maintenance-mode" >}}))
- **Start epoch sealing buffer**: Verify if the start epoch is respected ([doc]({{< ref "storage-providers/manage/others/index.md#start-epoch-sealing-buffer" >}}) )

- **Rate limits**: Ensure that the client and/or global rate limits have not been exceeded ([doc]({{< ref "storage-providers/manage/others/index.md#limits" >}}) )

- **Storage acceptance logic**: Dynamically apply the storage acceptance logic defined ([doc]({{< ref "storage-providers/manage/storage-acceptance-logic/index.md" >}}) )

Upon failure of any of these components, the proposal is directly rejected.
The proposal must pass all the components to be accepted.

In case  the deal is rejected : 
- An intenal detailed  decision message is logged to CIDgravity (accessible via the [History]({{< ref "storage-providers/analytics/history/index.md" >}})) and logged to the CIDgravity connector (on the miner).
-  A simplified comprehensive error message is sent to the client (through Curio,Boost/Venus).
