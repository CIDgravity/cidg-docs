---
title: "Advanced operations"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-advanced-operations"
weight: 104
toc: true
---

Storage acceptances logic also accept operations between variables. They will allow you to combine several 
of them to create advanced logic that can meet all needs

## Supported operations

- `Sum`
- `Substraction`
- `Multiplication`
- `Division`

{{< alert icon="warning" >}}
All operations only support a maximum of 2 variables. On the other hand, the operations can be chained together to give something like VariableA + (VariableB + VariableC), which is equivalent to VariableA + VariableB + VariableC
{{< /alert >}}

{{< alert icon="tip" >}}
In the same way, if you want to do VariableA + VariableB - VariableC, you can add on the same rule, an addition and a subtraction
{{< /alert >}}

## How to add an operation to a rule ?

You can by adding by clicking on `⋮` and selecting `Advanced operations`

In the drop-down menu that will appear, you can choose among the operations supported by the storage acceptance logics

![Add advanced operation to a storage acceptance logic rule](add-advanced-operations.png)
