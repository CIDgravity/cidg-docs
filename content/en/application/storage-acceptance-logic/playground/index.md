---
title: "Simulate a logic"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-playground"
weight: 104
toc: true
---

As with pricing rules, it is possible to simulate a storage acceptance logic

This makes it possible to validate that it corresponds in every way to what it must filter before applying it to incoming deals.

## Fill variables

To do this, go to the Playground (Storage > Playground in the side menu)

In the first block, you must fill in all the elements specific to the proposal (client, price, size, start epoch, etc.)
And in the second block, you can simulate all the values of the sealing pipeline

{{< alert icon="tip" >}}
There are no limits in the number of items that can be added. You can add new ones with the "Add new value" button
{{< /alert >}}

![Fill variable to simulate a storage acceptance logic](fill-variables-playground.png)

## Interpret the result

In the event that your proposal is rejected due to the storage acceptance logic applied, this will be displayed in the results box on the right

{{< alert icon="tip" >}}
All variables have been automatically replaced with applied values to help you understand what went wrong
{{< /alert >}}

In the case of a storage acceptance logic which would be equivalent to something like :

```json
{
   "and":[
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

The simulation would result in a failure, with the following result on the right screen:

```json
{
  "and": [
    {
      ">=": [
        7,
        10
      ]
    },
    {
      "<=": [
        0,
        2
      ]
    }
  ]
}
```

Indeed, this proposal was rejected, because the value specified on the Playground is `PC1 == 7` and the storage acceptance logic requests `PC1 >= 10`

You can perform as much simulation as necessary to define the logic that will work best.