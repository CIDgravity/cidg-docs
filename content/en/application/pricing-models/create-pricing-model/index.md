---
title: "Create new pricing model"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
lead: "This guide describes how you can create a pricing model in CIDgravity"
draft: false
images: []
menu:
    application:
        parent: "application-pricing-models"
        identifier: "application-pricing-models-create"
weight: 101
toc: true
---

You can navigate in the sidebar under `Storage` > `Pricing`

On the top, you can click on `Create a new model`

### 1. Define a name

To better recognize the specifics of the pricing model, you can define the name you want. 
For example `All 16 GiB verified deals at 0`

![Set the pricing model name and the fallback behavior](set-name-and-fallback.png)

### 2. Define the fallback behavior

If the rules of this pricing model do not match the incoming deal, it is possible to automatically apply the default model

{{< alert icon="warning" >}}
If this option is disabled, the deal will be directly rejected after evaluating this pricing model, otherwise, the default 
model will be applied to make a decision
{{< /alert >}}

### 3. Create the rules

For a model to be complete, it must be composed of one or more rules that will apply to an incoming proposal

{{< alert icon="warning" >}}
All rules will be browsed in order from top to bottom, pay attention to their location
{{< /alert >}}

To create a rule, several elements are available, and all of them will be evaluated together to define if the rule matches:

- **Type**: filter on the TransferType field allowed
- **Verified**: define if this rule accept verified, unverified or both deals 
- **Size**: defines the size range allowed to apply this rule. It is possible to define it in different units
- **Duration**: defines the duration range allowed to apply this rule. It is possible to define it in different units
- **Price**: the minimum price required for a deal that meets all the criteria of this rule (must be specified in FIL / GiB / Epoch)

{{< alert icon="tip" >}}
If at least one of the criteria of a rule is not respected, the next one will be evaluated, and so on until going through all of them
{{< /alert >}}

![Example of one rule that compose a pricing model](rule-example.png)
