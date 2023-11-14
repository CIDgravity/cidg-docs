---
title: "Overview"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide serves as an introduction to the capability of establishing acceptance rules that are contingent on pipeline sealing status"
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-overview"
weight: 100
toc: true
---

To access this module, you can navigate through the sidebar menu by selecting `Storage` and then `Acceptance logic`

{{< alert icon="warning" >}}
This feature will exclusively works for online deals and requires the miner to be configured to utilize Boost node with a version equal or greater than 2.1.0
{{< /alert >}}

## What is a storage acceptance logic ?

This entails the establishment of a rule-based system for the determination of transaction approval or rejection, contingent on a diverse criterias, which encompasses:

- Sealing Pipeline State
- Temporal factors, encompassing both the time of day and daytime considerations.
- FIL price (to be introduced in the near future)
- Disk Space Availability (to be introduced in the near future)
- Concurrent Download Thresholds (to be introduced in the near future)

Furthermore, it is imperative to underline that a storage acceptance algorithm is concurrently applied alongside the pricing model.

The storage acceptance logic accommodates the following parameters:
- [Variables](../available-values)
- Values
- [Advanced operations](../advanced-operations)
- [Comparison signs](../comparison-signs)

## How does it works ?

When crafting a storage acceptance logic within CIDgravity, a JSON-formatted logic is generated and subsequently applied upon the arrival of a proposal. 

Here is an illustrative example of an applied JSON logic:

```json
{
   "or":[
      {
         ">=":[
            {
               "var":"PreCommit1"
            },
            10
         ]
      },
      {
         "<=":[
            {
               "var":"PreCommit2"
            },
            2
         ]
      }
   ]
}
```

## Testing 

The acceptance logic can be rigorously tested within the Playground. 
When simulating a deal proposal from this environment, it is feasible to replicate the miner's state at the moment of proposal reception, which may include variables such as the number of concurrent PC1 deals.

This simulation allows for a comprehensive assessment of how the acceptance logic will respond and behave in a real-world scenario.

