---
title: "Dashboard"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-analytics"
        identifier: "storage-providers-analytics-dashboard"
weight: 100
toc: true
---

On CIDgravity, you can find 3 different dashboards

## Miner availability

When enabling the Miner Status Check option, CIDgravity simulates storage deals by periodically sending test proposals. 
This process measures miner availability and assesses the state of the sealing pipeline.

These information are used for : 

- evaluating in correlation to the miner settings, if the miner is ready to receive new deals from client.
- providing the miner status dashboard. This dashboard supersedes the default dashboard. It provides a real-time and historical overview of miner availability, balances, sealing pipeline activity, and other pertinent metrics.

To enable this functionality, navigate to `Settings` > `Automatic Miner Status Check`. 

### Sealine pipeline panel

{{< img src="sealing-pipeline-chart.png" alt="Sealine pipeline chart dashboard" height=1068 >}}

To enhance the clarity and readability of a miner's sealing pipeline status, certain sector states have been grouped into the following categories:

| State | Groups
| ----- | ----- |
| WaitDeals | WaitDeals, SnapDealsWaitDeals
| AP | Packing, AddPiece, SnapDealsAddPiece, SnapDealsPacking
| Error | CommitFinalizeFailed, FailedUnrecoverable, SealPreCommit1Failed, SealPreCommit2Failed, PreCommitFailed, ComputeProofFailed, RemoteCommitFailed, CommitFailed, PackingFailed, FinalizeFailed, SnapDealsAddPieceFailed, ReplicaUpdateFailed, ReleaseSectorKeyFailed, FinalizeReplicaUpdateFailed, AbortUpgrade
| WaitChain | GetTicket, PreCommitting, PreCommitWait, SubmitPreCommitBatch, PreCommitBatchWait, WaitSeed, SubmitCommit, SubmitCommitAggregate, CommitAggregateWait, SubmitReplicaUpdate, WaitMutable, ReplicaUpdateWait, ReplicaUpdateWait
| PC1 | PreCommit1
| PC2 | PreCommit2
| C1/C2 | Committing, CommitFinalize
| FIN | FinalizeSector, UpdateActivating, ReleaseSectorKey, FinalizeReplicaUpdate
| RU | UpdateReplica
| PR1/PR2 | ProveReplicaUpdate

{{< alert icon="tip" >}}
Sectors that do not appear in the provided table have been removed and are excluded from the graph's count.
{{< /alert >}}

## Storage analytics

The storage analytics dashboard can be found under `Storage` > `Analytics`
On this dashboard, you will find important metrics related to the storage market:

- reasons of rejection
- top 10 clients for both accepted and rejected deals
- repartition of deal params for both accepted and rejected deals
- historical view for many metrics

{{< figure src="storage-analytics.png" alt="Storage analytics dashboard" width=850 >}}

## Retrieval analytics

The storage analytics dashboard can be found under `Retrieval` > `Analytics`
On this dashboard, you will find important metrics related to the retrieval market:

- reasons of rejection
- top 10 peer id for both accepted and rejected retrieval deals
- historical view for the number of deals (accepted and rejected)

{{< figure src="retrieval-analytics.png" alt="Retrieval analytics dashboard" width=700 >}}