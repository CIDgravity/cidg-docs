---
title: "Overview"
description: "This guide introduces the functionality to set acceptance rules based on pipeline sealing status"
lead: "This guide introduces the functionality to set acceptance rules based on pipeline sealing status, such as number of deals in PC1 and more."
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-overview"
weight: 100
toc: true
---

To access this module you can use the sidebar menu under Storage > Acceptance logic

{{< alert icon="warning" >}}
This feature will works only for Online deals, and if the miner is configured to use boost node, with version after 2.1.0 !
{{< /alert >}}

## What is a storage acceptance logic ?

It's a set of rules that can be defined to accept or reject deals based on a various set of factors :
    - Sealing Pipeline State
    - Time of the day / day time
    - Fil price (coming soon)
    - Available disk space (coming soon)
    - Concurrent downloads (coming soon)
    
A storage acceptance logic applies in addition to a pricing model.

The storage acceptance logic accepts folowing parameters : 
- [`Variables`]({{< relref "../available-values" >}})
- `Values`
- [`Advanced operations`]({{< relref "../advanced-operations" >}})
- [`Comparison signs`]({{< relref "../comparison-signs" >}})

## How does it works ?

When you create a storage acceptance logic on CIDgravity, a logic in JSON format is generated and applied when a proposal arrives

Here is an example of applied JSON logic:

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

Acceptance logic can be tested from the Playground. 
When simulating a deal proposal from the playground, its possible to simulate the miner's state (Number of concurrent PC1 as an example) at the time you receive the proposal and confirm how the Acceptance logic will behave.
