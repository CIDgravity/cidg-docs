---
title: "Others"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-others"
weight: 299
toc: true
---

## Maintenance mode

Maintenance mode provides an easy and fast way to stop accepting any kind of deals  : storage, retrieval (graphsync / bitswap / http). 

The activation of maintenance mode take effect immediatelly and results in the automatic rejection of all deals. 

To toggle maintenance mode on or off, utilize the switch located on the top navigation bar.

{{< img src="maintenance-mode.png" alt="Enable and disable the maintenance mode" >}}

## Limits

Limits serve as a protective measure for the miner, preventing the sealing pipeline to be overloaded. 

Limits are implemented at 2 levels : 
	- Global limits apply accross all clients. Any accepted deals from any clients will be counted in the same bucket. If that bucket exceed the limit, nor more deals are accepted. 	
	- Client limits only apply to a specific client. All deals of that client are counted to evaluat if new deals should be accepted. When a limit is set on a client; both the client rate limit and the global rate limit are evaluated.

{{< alert icon="warning" >}}
The global limits should be set to the maximum ingestion capacity of the miner.
{{< /alert >}}

These limits are applied to any clients registred or unknown.

Any new deals are rejected as long as the limit of accepted deals is exceeded.

For configuration of the global limits, navigate to the `Settings` > `Global rate limits`.

{{< img src="global-rate-limits.png" alt="Configure the global rate limits" >}}

Various rate limits can be configured:

- **Number of storage deals per hour**: The maximum number of storage deals accepted over the last 60 minutes.
- **Cumulative storage deal size per hour**: The maximum cumulative storage deal size (GiB) accepted over the last 60 minutes.
- **Retrieval deals per hour**: The maximum number of graphsync retrieval deals accepted over the last 60 minutes.

{{< alert icon="warning" >}}
Limits are calculated over the last 60 minutes and reevaluated in realtime on each new proposal received.
{{< /alert >}}

{{< alert icon="tip" >}}
Set a limit to 0 to disable it (unlimited).
{{< /alert >}}

## Start epoch sealing buffer

The start epoch sealing buffer setting allow to reject deals if a deal start epoch is under a specific requirement.

This feature will reject any deals that doesn't provide enough time to be processed. 

To configure the start epoch sealing buffer, navigate to the `Settings` section, specifically under `Start epoch sealing buffer`.

{{< img src="start-epoch-sealing-buffer.png" alt="Configure the start epoch sealing buffer" >}}

For example, if the value set is 24 hours, it means all deals with a `start epoch < current chain epoch - 1880 (number of epochs in 24 hours)` will be rejected

{{< alert icon="warning" >}}
The value is expressed in hours
{{< /alert >}}

{{< alert icon="warning" >}}
It's possible to override the start epoch sealing buffer for any registerd clients. Simply by editing the client.
{{< /alert >}}
