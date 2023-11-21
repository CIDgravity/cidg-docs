---
title: "Others"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-others"
weight: 105
toc: true
---

## Maintenance mode

Activation of maintenance mode results in the automatic rejection of all deals received by a miner. 
This option is applicable to both storage and retrieval deals. 

To toggle maintenance mode on or off, utilize the switch located on the top navigation bar.

{{< img src="maintenance-mode.png" alt="Enable and disable the maintenance mode" >}}

## Global limits

Global limits serve as a protective measure for the miner, preventing an influx of deals within a short timeframe. 
These limits are applied without regard to the customer's status, whether registered or not.

In the event these limits are exceeded, all deals processed by CIDgravity will be rejected.

For configuration of the global limits, navigate to the `Settings` section, specifically under `Global rate limits`.

{{< img src="global-rate-limits.png" alt="Configure the global rate limits" >}}

Various rate limits can be configured:

- **Number of storage deals per hour**: sets the maximum allowable number of storage deals
- **Cumulative storage deal size per hour**: defines the maximum cumulative size of all deals that can be received within an hour
- **Retrieval deals per hour**: establishes the maximum allowable number of retrieval deals

{{< alert icon="warning" >}}
All limits are calculated over a rolling hour, ensuring a dynamic and continuous evaluation of the specified constraints within the preceding 60-minute timeframe.
{{< /alert >}}

{{< alert icon="tip" >}}
To signify no specified limits, you can enter 0, indicating an unrestricted or unlimited setting for the corresponding parameter.
{{< /alert >}}

## Start epoch sealing buffer

The start epoch sealing buffer setting allow to reject deals if a deal start epoch is under a specific requirement
This option will filter incomming storage deals to give time for sealing of sector with deal.

To configure the start epoch sealing buffer, navigate to the `Settings` section, specifically under `Start epoch sealing buffer`.

{{< img src="start-epoch-sealing-buffer.png" alt="Configure the start epoch sealing buffer" >}}

For example, if the value set is 24, it means all deals with a `start epoch < current chain epoch - 1880 (number of epochs in 24 hours)` will be rejected

{{< alert icon="warning" >}}
The value must be expressed in hours
{{< /alert >}}

{{< alert icon="warning" >}}
It's possible to define start epoch sealing buffer for any registerd clients. To set client specific option, just edit a client
{{< /alert >}}
