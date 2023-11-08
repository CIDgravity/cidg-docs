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

The storage acceptances logic also supports operations between variables, enabling you to combine multiple variables to construct advanced logic that can 
accommodate a wide range of requirements.

## Supported operations

- `Sum`
- `Substraction`
- `Multiplication`
- `Division`

{{< alert icon="warning" >}}
Each operation is limited to a maximum of 2 variables, but you can chain operations together to achieve the desired results. For example, you can create expressions like `VariableA + (VariableB + VariableC)`, which is equivalent to `VariableA + VariableB + VariableC`
{{< /alert >}}

{{< alert icon="tip" >}}
To perform operations like VariableA + VariableB - VariableC, you can incorporate both addition and subtraction within the same rule
{{< /alert >}}

## How to add an operation to a rule ?

To access advanced operations for storage acceptance logic, you can click on the ellipsis icon (`⋮`) and then select `Advanced operations` from the dropdown menu. 
This will open a menu where you can choose from a range of operations supported by the storage acceptance logic

![Add advanced operation to a storage acceptance logic rule](add-advanced-operations.png)
