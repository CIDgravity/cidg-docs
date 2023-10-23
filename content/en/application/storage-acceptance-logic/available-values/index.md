---
title: "Available values"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-available-values"
weight: 101
toc: true
---

When creating new storage acceptance logic, several variables are offered.
It is possible to combine them in order to define an even more advanced logic

## Sealing pipeline

These variables correspond to those of the sealing pipeline.

They are included in the Boost proposals:

{{< alert icon="tip" >}}
The applicable unit for sealing pipeline variables is a deal number (integer)
{{< /alert >}}

| Value | Description
| --- | --- | --- |
| WaitDeals | waiting for more pieces (deals) to be added to the sector
| Packing | sector not in sealStore, and not on chain
| AddPiece | put deal data (and padding if required) into the sector
| AddPieceFailed | /
| GetTicket | generate ticket
| PreCommit1 | do PreCommit1
| PreCommit2 | do PreCommit2
| PreCommitting | on chain pre-commit (deprecated)
| PreCommitWait | waiting for precommit to land on chain
| SubmitPreCommitBatch | /
| PreCommitBatchWait | /
| WaitSeed | waiting for seed
| Committing | compute PoRep
| CommitFinalize | cleanup sector metadata before submitting the proof (early finalize)
| CommitFinalizeFailed | /
| SubmitCommit | send commit message to the chain
| SubmitCommitAggregate | /
| CommitAggregateWait | /
| FinalizeSector | /
| Proving | /
| Available | proving CC available for SnapDeals
| FailedUnrecoverable | /
| SealPreCommit1Failed | /
| SealPreCommit2Failed | /
| PreCommitFailed | /
| ComputeProofFailed | /
| RemoteCommitFailed | /
| CommitFailed | /
| PackingFailed | /
| FinalizeFailed | /
| DealsExpired | /
| RecoverDealIDs | /
| Faulty | sector is corrupted or gone for some reason
| FaultReported | sector has been declared as a fault on chain
| FaultedFinal | fault declared on chain
| Terminating | /
| TerminateWait | /
| TerminateFinality | /
| TerminateFailed | /
| Removing | /
| RemoveFailed | /
| Removed | /
| SnapDealsWaitDeals | snap deals / cc update
| SnapDealsAddPiece | snap deals / cc update
| SnapDealsPacking | snap deals / cc update
| UpdateReplica | snap deals / cc update
| ProveReplicaUpdate | snap deals / cc update
| SubmitReplicaUpdate | snap deals / cc update
| WaitMutable | snap deals / cc update
| ReplicaUpdateWait | snap deals / cc update
| UpdateActivating | snap deals / cc update
| ReleaseSectorKey | snap deals / cc update
| FinalizeReplicaUpdate | snap deals / cc update
| SnapDealsAddPieceFailed | /
| SnapDealsDealsExpired | /
| SnapDealsRecoverDealIDs | /
| ReplicaUpdateFailed | /
| ReleaseSectorKeyFailed | /
| FinalizeReplicaUpdateFailed | /
| AbortUpgrade | /
| ReceiveSector | for external import

## Other variables

In addition, variables calculated at the time of receipt of the proposal are available.

They can also be included in each storage acceptance logic:

| Value | Description | Unit
| --- | --- | --- |
| ReceivedOn | epoch at which the proposal is analyzed by CIDgravity | ChainEpoch

{{< alert icon="success" >}}
More variables will be available in future versions of CIDgravity
{{< /alert >}}

