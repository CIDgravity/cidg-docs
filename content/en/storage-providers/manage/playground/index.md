---
title: "Playground"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-playground"
weight: 104
toc: true
---

To access this module, you can navigate through the sidebar menu by selecting `Storage` and then `Playground`

Using playground, you can simulate all your criterias's accuracy before its actual application to incoming deal proposals.

## Fill deal proposal details

In the initial block, input all the relevant details specific to the proposal, such as client information, pricing, data size, start epoch, and other pertinent parameters.

{{< img src="fill-proposal-details.png" alt="Fill the deal proposal details" >}}

{{< alert icon="tip" >}}
For the client address, you can choose between registered clients, or use any Filecoin address
{{< /alert >}}

## Fill acceptance logic details

In the second block, you have the ability to simulate and configure various values related to the sealing pipeline

You can seamlessly include additional items by utilizing the `Add new value` button as needed

{{< alert icon="tip" >}}
There are no restrictions on the number of items that can be added
{{< /alert >}}

{{< img src="fill-variables-playground.png" alt="Fill variable to simulate a storage acceptance logic" >}}

## Analyse the result

### Acceptance

If the proposal is accepted, a green success mark will be display on the right.

You will also find the pricing model and the storage acceptance logic used for this deal

{{< img src="success-accepted.png" alt="Deal proposal has been accepted" >}}

### General rejection

If the proposal has been rejected, you will find the reason in the box located on the right

{{< img src="error-rejected.png" alt="Deal proposal has been rejected" >}}

### Acceptance logic rejection

In the event that your proposal faces rejection as a consequence of the applied storage acceptance logic, the rejection status will be prominently displayed in the results box located on the right-hand side.

{{< alert icon="tip" >}}
All variables are automatically substituted with the actual values used in the simulation, which aids in providing a clear understanding of the specific reasons for the rejection, thus facilitating the debugging and troubleshooting process.
{{< /alert >}}

For example, using the following storage acceptance logic:

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

Will result in proposal to be rejected and the right-hand screen would display the following result:

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

The rejection of this proposal is attributed to the mismatch between the value set in the Playground, which is `PC1 == 7`, 
and the stipulated requirement in the acceptance logic, which is `PC1 >= 10`.
