---
title: "Pricing"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide provides instructions on managing pricing models."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-pricing"
weight: 201
toc: true
---

Access `Storage` > `Pricing`.

A pricing model is a group of rules where each rule associates a price to certains types of deals.
There is no limit on the number of rules per pricing model. 

When a new deal proposal is reaching the pricing engine, the rules engine look for the first matching pricing rule, verify the price and exit with a decision.
Rules are processed top to bottom.


## Flow chart

```goat
                    +---------------+
                    | Deal proposal |
                    +--------+------+
                             |
                      +------+-------+
                      | Match client |
                      +-+----------+-+
                        |          |                 +----+
                      Found    Not Found             |    |
                        |          |                 |    |
                        v          v                 v    |
   +------------------------+ +-------------------------+ |
   | Process Client Pricing | | Process Default Pricing | |
   +--------------------+---+ +----+--------------------+ |
                        |          |                      |
                        v          v                      |
                      +--------------+                    |
                      | Match  rules |                    |
                      +-+----------+-+                    |
                        |          |                      |
                      Found    Not Found                  |
                        |          |                      |
                        v          v                      |
            +---------------+ +-----------------+         |
            | Is Deal price | | Is Fallback to  |         |
            | >= Rule price | | default pricing |         |
            +--+--------+---+ +----+--------+---+         |
               |        |          |        |             |
              Yes       No         No      Yes            |
               |        |          |        |             |
               |        v          v        +-------------+
               |     +---------------+
               |     | Deal rejected |
               |     +---------------+
               v
   +----------------+
   | Price accepted |
   +--------+-------+
            |
            v
+----------------------+
| Process next         |
| CIDgravity component |
+----------------------+
```

## Default pricing model

It's a special pricing applying to :
- Deals from Filecoin address not attached to any registered clients.
- Any client with no specific pricing model set.

The default pricing model cannot be removed, first set another pricing model as default before deletion.

## Create new model

Click on the `Create a new model` button at the top.

#### 1. Pricing name

For a more granular understanding of the pricing model, you have to set the desired name. 
As an illustration, you can specify a name such as `All 16 GiB verified deals at 0`

{{< img src="set-name-and-fallback.png" alt="Set the pricing model name and the fallback behavior" >}}

#### 2. Fallback behavior

This feature is interesting, when a specific client, have a specific pricing or specific type of deals on top of what you offer by default.

The incoming deal is first evaluated against the client pricing model, if no rules match, it's evaluated against the default pricing model. 

The "Fallback to default pricing model" setting is ignored when a pricing is set as the default pricing model.

#### 3. Rules creation

To match a rule, a deal needs first to fill all conditions except the price, then the price is compared.

- **Type**: Deal TransferType : graphSync, HTTP, libP2P, etc, offline ...
- **Verified**: Verified(Fil+) or unverified deals
- **Size**: Padded Deal size range (PieceSize)
- **Duration**: Deal duration(EndEpoch-StartEpoch)
- **Price**: Minimum price in FIL/GiB/Epoch.

{{< alert icon="tip" >}}
Rules order matter, they can be easily reorganised with drag and drop.
{{< /alert >}}

{{< img src="rule-example.png" alt="Example of one rule that compose a pricing model" >}}

## Manage existing models

{{< img src="models-list.png" alt="Manage pricing models using the pricing models management page" >}}

Each pricing model listed offers several options:

- **View**: Quick access to the pricing rules.
- **Edit**
- **Remove**
- **Set as default**: Establishes the chosen pricing model as default. 

{{< alert icon="tip" >}}
A pricing set as default or attached to client cannot be deleted.
{{< /alert >}}

