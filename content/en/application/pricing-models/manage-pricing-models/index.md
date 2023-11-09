---
title: "Manage pricing models"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
lead: "This guide describes how you can manage pricing models"
draft: false
images: []
menu:
    application:
        parent: "application-pricing-models"
        identifier: "application-pricing-models-manage"
weight: 100
toc: true
---

You can navigate in the sidebar under `Storage` > `Pricing`

![Manage pricing models using the pricing models management page](models-list.png)

For each pricing model in the list, there are have several options : 

- **View**: to consult all the rules that make up the pricing model
- **Edit**: to modify one or more rules
- **Remove**: to delete it
- **Set as default**: to set the selected pricing model as the default

{{< alert icon="tip" >}}
It's not possible to remove the default pricing model, in order to remove it, set another model as default before
{{< /alert >}}

{{< alert icon="warning" >}}
Also, it's not possible to remove a pricing model attached to a client. Edit the client before, and ensure that no one uses it
{{< /alert >}}