---
title: "Miner status dashboard"
description: "CIDgravity application serves as a comprehensive tool for managing settings, clients, and the acceptance rules of pricing models"
draft: false
images: []
menu:
    application:
        parent: "application-analytics"
        identifier: "application-analytics-miner-status"
weight: 101
toc: true
---

The miner status dashboard is contingent upon the activation of the miner status checker option within the miner's settings

{{< alert icon="tip" >}}
The status checker service provided by CIDgravity operates by periodically sending mock proposals or requests to a miner to assess its availability and collect crucial information. These simulated requests help in monitoring the miner's responsiveness and ensuring that it remains active and accessible.
{{< /alert >}}

## Sealing pipeline chart

To enhance the clarity and readability of a miner's sealing pipeline status, certain sector states have been grouped into the following categories:

| Original sector state | Groupped as
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
Sectors that do not appear in the provided table have been removed and are excluded from the graph's count
{{< /alert >}}