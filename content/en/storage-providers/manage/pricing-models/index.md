---
title: "Pricing"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide provides instructions on managin the pricing models."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-pricing"
weight: 101
toc: true
---

## Manage existing models

To access the pricing section, you can navigate through the sidebar by selecting `Storage` and then `Pricing`.

![Manage pricing models using the pricing models management page](models-list.png)

Each pricing model listed offers several options:

- **View**: Allows you to review all the rules constituting the pricing model
- **Edit**: Permits modification of one or more rules within the model
- **Remove**: Enables deletion of the selected pricing model
- **Set as default**: Establishes the chosen pricing model as the default configuration

{{< alert icon="tip" >}}
The removal of the default pricing model is restricted. 
To delete it, first, designate another model as the default and then proceed with the removal of the desired default model.
{{< /alert >}}

{{< alert icon="warning" >}}
The removal of a pricing model linked to a client is constrained. 
Prior to attempting removal, edit the associated client details and ensure that it is not currently in use.
{{< /alert >}}

## Create new model

You can use sidebar by selecting the `Storage` tab and further navigating to the `Pricing` section.

At the apex, you have the option to initiate the creation of a new model by clicking on the `Create a new model` button at the top.

#### 1. Define a name

For a more granular understanding of the pricing model, you have to set the desired name. 
As an illustration, you can specify a name such as `All 16 GiB verified deals at 0`

![Set the pricing model name and the fallback behavior](set-name-and-fallback.png)

#### 2. Define the fallback behavior

If the rules of the pricing model fail to align with the incoming deal, there exists the capability to automatically use the default model.

{{< alert icon="warning" >}}
In the scenario where this option is deactivated, the deal undergoes direct rejection when this pricing model has been applied. 
With this option enabled, the default model is invoked to facilitate the decision-making process.
{{< /alert >}}

#### 3. Create the rules

For a model to achieve completeness, you need to create one or more rules designed to be applicable to incoming proposals.

{{< alert icon="warning" >}}
The rules will be applied from top to bottom, so careful attention should be paid to their respective order.
{{< /alert >}}

In the rule creation process, multiple elements can be use, and their collective evaluation determines whether the rule is a match :

- **Type**: Enables filtering based on the allowed values in the TransferType field.
- **Verified**: Specifies whether this rule accepts verified, unverified, or both types of deals.
- **Size**: Establishes the permissible size range for applying this rule, with the flexibility to define units in various formats.
- **Duration**: Sets the acceptable duration range for applying this rule, providing the option to express it in different units.
- **Price**: Establishes the minimum price prerequisite for a deal that satisfies all the criteria outlined in this rule, with the specification in FIL/GiB/Epoch.

{{< alert icon="tip" >}}
In the evaluation process of a rule, if any single criterion is not met, subsequent criteria will be assessed sequentially.
This sequential evaluation continues until all specified criteria have been examined.
{{< /alert >}}

![Example of one rule that compose a pricing model](rule-example.png)
