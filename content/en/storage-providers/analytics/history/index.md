---
title: "History"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-analytics"
        identifier: "storage-providers-analytics-history"
weight: 101
toc: true
---

In the history, you can find the list of all the deals received by a miner, with all of its information, as well as the decision taken by CIDgravity

{{< alert icon="tip" >}}
For all histories, you can use multiple filters, such as decision, date, client name or address, pricing and more
{{< /alert >}}

## Storage history

To access storage historys navigate under `Storage` > `History`
You will find a paginated list of all storage deals received by the selected miner

For each deal listed, various options are available:

- **Inspect deal proposal**: will display the entire deal proposal received as JSON format (valid proposal only)
- **Simulate in playground**: will load this deal proposal on playground and simulate the storage deal processing on it (valid proposal only)
- **Inspect acceptance logic**: will display the acceptance logic that failed for this deal (rejected proposal only)

{{< img src="storage-history.png" alt="Storage history" >}}

## Retrieval history

To access storage historys navigate under `Retrieval` > `History`
You will find a paginated list of all retrieval deals received by the selected miner

For each deal listed, you will have the option to Inspect the deal proposal. This will display the entire retrieval proposal received as JSON format

{{< img src="retrieval-history.png" alt="Retrieval history" >}}
