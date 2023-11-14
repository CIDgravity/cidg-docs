---
title: "Miner status dashboard"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    application:
        parent: "application-analytics"
        identifier: "application-analytics-miner-status"
weight: 101
toc: true
---

When enabling the `Miner Status Check` option, CIDgravity simulates storage deals by periodically sending test proposals. This process measures miner availability and assesses the state of the sealing pipeline.

These information are used for : 

- evaluating in correlation to the miner settings, if the miner is ready to receive new deals from client.
- providing the miner status dashboard. This dashboard supersedes the default dashboard. It provides a real-time and historical overview of miner availability, balances, sealing pipeline activity, and other pertinent metrics.

To enable this functionality, navigate to `Settings` > `Automatic Miner Status Check`. 

## Sealing pipeline panel

XXX INSERT SEALIGN PIPELINE EXEMPLE HERE

To enhance the clarity and readability of a miner's sealing pipeline status, certain sector states have been grouped into the following categories:

| Sector state | Groups
| --- | --- |
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
