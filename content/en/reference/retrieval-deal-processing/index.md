---
title: "Retrieval deal processing"
description: "This section explain how the retrieval deals are processed by CIDgravity using clients configuration"
draft: false
images: []
menu:
    reference:
        parent: "reference-retrieval-deal-processing"
        identifier: "reference-retrieval-deal-processing-overview"
weight: 102
toc: true
---

Deals processing is a core component of CIDgravity, most of the features in CIDgravity will impact the acceptance of a deal. Through this article you will understand how all these components will work together to get the best out CIDgravity.

The decision outcome is binary:

- `Accept`: The proposal successfully meets all criteria, allowing for processing by Lotus/Boost.
- `Reject`: The proposal fails to satisfy one or more criteria, leading to rejection. The rejection reason is explicitly specified in the response.

## How does it works ?

{{< img src="retrieval-deal-flow.png" alt="Retrieval deal flow in CIDgravity" >}}

When a deal is received and passed by Boost/Venus to CIDgravity, it follows the workflow below :

- **Proposal integrity**: verify the integrity of the incoming proposal 
	- integrity checks
	- format
	- value threshold
	- etc...
- **Client identification and authorization**: identify the client associated with the incoming deal and grant authorization based on the libP2P address (for graphsync and bitswap, does not apply to HTTP)

- **Maintenance mode**: evaluate whether the miner is currently in maintenance mode ([doc]({{< ref "storage-providers/manage/others/index.md#maintenance-mode" >}}))

- **Rate limits**: Ensure that the global retrieval rate limit have not been exceeded ([doc]({{< ref "storage-providers/manage/others#global-limits/index.md" >}}) )


Upon failure of any of these components, the proposal is directly rejected.
The proposal must pass all the components to be accepted.

In case  the deal is rejected : 
 - An intenal detailed  decision message is logged in CIDgravity (accessible via the ```history``` page and logged to the CIDgravity connector (on the miner).
-  A simplified comprehensive error message is sent to the client (through Boost/Venus).

{{< alert icon="callout" >}}
The order is important because if a test fails, subsequent steps will not be analyzed.
{{< /alert >}}
