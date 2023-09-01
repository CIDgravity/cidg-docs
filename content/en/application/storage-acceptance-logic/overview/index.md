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

It's a set of rules that can be defined to accept or reject a deal. It's similar to pricing models, except that the storage acceptance logic 
has more to protect and limit the number of deals coming to a miner.

A storage acceptance logic applies in addition to the pricing rules defined in the Pricing models

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

## When is it applied ?

Storage acceptance logic is applied after global limits and maintenance mode, but before pricing rules.

In the case where the proposal that arrives does not match the storage acceptance logic, it is automatically rejected and the pricing rules will not apply

If the proposal is rejected, it will be recorded on your dashboards in the `Storage acceptance logic not passed` category.