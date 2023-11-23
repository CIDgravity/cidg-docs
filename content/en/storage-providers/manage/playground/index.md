---
title: "Playground"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-playground"
weight: 204
toc: true
---

CIDgravity offers an infinite array of options to manage your acceptance criteria. It can be challenging to foresee how all these parameters will interact. To address this, we introduce the playground, which aids in validating the entire storage deals pipeline. It lets yous imulate the pipeline states and send dummy proposals to the CIDgravity engine and get detailled result.

You can either access the playground directly from :
- the side bar : `Storage` > `Playground`
- any past proposals from the `History`. If so the playground will be automatically populated with the proposal's values.


## Fill deal proposal details

In the initial block, input all the proposal information, such as client address, pricing, data size, start epoch, ...

{{< img src="fill-proposal-details.png" alt="Fill the deal proposal details" >}}

{{< alert icon="tip" >}}
For the client address, you can choose between registered clients, or use any Filecoin address
{{< /alert >}}

## Fill acceptance logic details

In the second block, you have the ability to simulate and configure various values related to the sealing pipeline state

You can seamlessly include additional items by utilizing the `Add new value` button as needed

Lets say you want to simulate what happen when you send a proposal when there is already 20 ongoing PC1. Simply select the PC1 and set its value to 16.

{{< alert icon="tip" >}}
There are no restrictions on the number of items that can be added
{{< /alert >}}

{{< img src="fill-variables-playground.png" alt="Fill variable to simulate a storage acceptance logic" >}}

## Analyse the result

### Acceptance

If the proposal is accepted, a green success mark will be display on the right.

You will also get the information of the matching pricing model and storage acceptance logic.

{{< img src="success-accepted.png" alt="Deal proposal has been accepted" >}}

### General rejection

If the proposal has been rejected, you will find the reason in the box located on the right.

{{< img src="error-rejected.png" alt="Deal proposal has been rejected" >}}

### Acceptance logic rejection

In the event the proposal is rejected. The matching acceptance logic detailled resolution will be displayed. Need some practice but it's very powerful for understanding and troubleshooting acceptance logic.

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
and the requirement in the acceptance logic, which is `PC1 >= 10`.
