---
title: "Miner status dashboard"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
draft: false
images: []
menu:
    application:
        parent: "application-analytics"
        identifier: "application-analytics-miner-status"
weight: 101
toc: true
---

This dashboard is only available if the miner status checker option is enabled in the miner settings

{{< alert icon="tip" >}}
The status checker service offered by CIDgravity regularly sends false proposals to test the availability of a miner and retrieve essential information
{{< /alert >}}

## Sealing pipeline chart

To make the evolution of the state of a miner's sealing pipeline more readable, several sector states have been grouped into the same category.

Here are the groupings and categories available

| Sector state | Chart group
| --- | --- |
| WaitDeals | WaitDeals
| Packing | AP
| AddPiece | AP
| AddPieceFailed | Error
| GetTicket | WaitChain
| PreCommit1 | PC1
| PreCommit2 | PC2
| PreCommitting | WaitChain
| PreCommitWait | WaitChain
| SubmitPreCommitBatch | WaitChain
| PreCommitBatchWait | WaitChain
| WaitSeed | WaitChain
| Committing | C1/C2
| CommitFinalize | C1/C2
| CommitFinalizeFailed | Error
| SubmitCommit | WaitChain
| SubmitCommitAggregate | WaitChain
| CommitAggregateWait | WaitChain
| FinalizeSector | FIN
| FailedUnrecoverable | Error
| SealPreCommit1Failed | Error
| SealPreCommit2Failed | Error
| PreCommitFailed | Error
| ComputeProofFailed | Error
| RemoteCommitFailed | Error
| CommitFailed | Error
| PackingFailed | Error
| FinalizeFailed | Error
| SnapDealsWaitDeals | WaitDeals
| SnapDealsAddPiece | AP
| SnapDealsPacking | AP
| UpdateReplica | RU
| ProveReplicaUpdate | PR1/PR2
| SubmitReplicaUpdate | WaitChain
| WaitMutable | WaitChain
| ReplicaUpdateWait | WaitChain
| UpdateActivating | FIN
| ReleaseSectorKey | FIN
| FinalizeReplicaUpdate | FIN
| SnapDealsAddPieceFailed | Error
| ReplicaUpdateFailed | Error
| ReleaseSectorKeyFailed | Error
| FinalizeReplicaUpdateFailed | Error
| AbortUpgrade | Error

{{< alert icon="tip" >}}
All sectors states which are not present in the table have been deleted and are not counted on the graph
{{< /alert >}}