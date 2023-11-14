---
title: "Manage pricing models"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide provides instructions on managin the pricing models."
draft: false
images: []
menu:
    application:
        name: "Manage"
        parent: "application-pricing-models"
        identifier: "application-pricing-models-manage"
weight: 100
toc: true
---

To access the pricing section, you can navigate through the sidebar by selecting `Storage` and then proceeding to `Pricing`.

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
