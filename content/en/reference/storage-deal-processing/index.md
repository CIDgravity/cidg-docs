---
title: "Storage deal processing"
description: "This section explain how the incomming deals are processed by CIDgravity using clients, pricinglimits and acceptance logics configuration"
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

- `Accept`: The proposal successfully meets all criteria, allowing for processing by Boost/Venus.
- `Reject`: The proposal fails to satisfy one or more criteria, leading to rejection. The rejection reason is explicitly specified in the deal filter response.

## How does it works ?

When a deal is received and passed by Boost/Venus to CIDgravity, it follows the workflow below :

{{< img src="storage-deal-flow.png" alt="Storage deal flow in CIDgravity" >}}

- **Proposal integrity**: verify the integrity of the incoming proposal 
	- integrity checks
	- format
	- value threshold
	- etc...
- **Client identification and authorization**: identify the client associated with the incoming deal and grant authorization based on :
	- Deal acceptance from unknown clients
	- Client is blocked (more details on [client]({{< ref "storage-providers/manage/clients/index.md#manage-existing-clients" >}}) )
	- Blacklist (more details on [blacklists]({{< ref "storage-providers/manage/blacklist" >}}) )

- **Pricing model**: confirm the pricing is in line with the client pricing model :
	- Default pricing model for unknown clients
	- Client pricing model when the client is identified
	- Client pricing model followed by the default pricing model if the "Fallback to default pricing model is set on the client pricing model
- **Maintenance mode**: evaluate whether the miner is currently in maintenance mode (more details on [maintenance mode]({{< ref "storage-providers/manage/others/index.md#maintenance-mode" >}}))
- **Start epoch sealing buffer**: Verify if the start epoch is respected (more details on [start epoch sealing buffer]({{< ref "storage-providers/manage/others#start-epoch-sealing-buffer" >}}) )

- **Rate limits**: Ensure that the client and/or global rate limits have not been exceeded (more details on [global limits]({{< ref "storage-providers/manage/others#global-limits" >}}) )

- **Storage acceptance logic**: Dynamically apply the storage acceptance logic defined (more details on [storage acceptance logic]({{< ref "storage-providers/manage/storage-acceptance-logic)" >}}) )


Upon failure of any of these tests, the proposal is promptly rejected. 
Conversely, if none of the tests fail, the proposal is accepted and progresses for processing by the miner.

In the instance of rejection, a set of error codes may be returned to elucidate the specific reason for the rejection.

{{< alert icon="callout" >}}
The order is important because if a test fails, subsequent steps will not be analyzed.
{{< /alert >}}
