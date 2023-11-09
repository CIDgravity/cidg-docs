---
title: "Overview"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
lead: "This section will explain how the CIDgravity deal filter works"
draft: false
images: []
menu:
    application:
        parent: "application-deal-filter"
        identifier: "application-deal-filter-overview"
weight: 100
toc: true
---

The Deal Filter is the main feature of CIDgravity.

This is the component that filters all incoming (storage) and outgoing (retrieval) deals from a miner, based on the entire configuration:

- [`Clients`]({{< relref "../../clients/manage-clients" >}})
- [`Pricing models`]({{< relref "../../pricing-models/manage-pricing-models" >}})
- [`Storage acceptance logic`]({{< relref "../../storage-acceptance-logic/overview" >}})

It's responsible for analyzing all of these elements, to make a decision on the acceptance or rejection of the proposal that arrives.

The decision may be of two different natures:

- `Accept`: the proposal has been accepted because all criterias passed, the deal will be processed by Lotus / Boost
- `Reject`: the proposal does not meet one of your criteria, it is rejected, and the reason for rejection is specified in the deal filter response

## How does it works ?

The proposal is analyse with the folowing steps:

- Check proposal integrity
- Identify the client
- Apply rules for blacklist / client blocked
- Apply pricing model depending on the client who sent the deal
- Check if miner maintenance mode is enabled
- Check start epoch match the sealing buffer requirements
- Check that the client and / or global rate limits isn't reached
- Apply storage acceptance logic

If one these test failed, the proposal is directly rejected. Otherwise, if no one fail, the proposal is accepted and will be processed by the miner
In case of rejection, multiple error codes can be returned to explain the reason

{{< alert icon="callout" >}}
Te order is important, because if the test fail, the next step won't be analysed
{{< /alert >}}
