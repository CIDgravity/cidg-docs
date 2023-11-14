---
title: "Available values"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-available-values"
weight: 102
toc: true
---

When crafting new storage acceptance logic, you are presented with a variety of variables that you can use. These variables can be combined to formulate more advanced and sophisticated acceptance criteria. 

By leveraging the available variables and operations, you can design intricate and highly customized logic to govern how storage deals are accepted or rejected

## Sealing pipeline - sector states

These variables correspond to the states within the sealing pipeline, excluding errors or failed states

{{< alert icon="tip" >}}
The unit of measurement for sealing pipeline variables is typically a deal number, represented as an integer.
{{< /alert >}}

| Value | Description
| --- | --- | --- |
| WaitDeals | waiting for more pieces (deals) to be added to the sector
| Packing | sector not in sealStore, and not on chain
| AddPiece | put deal data (and padding if required) into the sector
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
| SubmitCommit | send commit message to the chain
| SubmitCommitAggregate | /
| CommitAggregateWait | /
| FinalizeSector | /
| Proving | /
| Available | proving CC available for SnapDeals
| FailedUnrecoverable | /
| DealsExpired | /
| RecoverDealIDs | /
| Faulty | sector is corrupted or gone for some reason
| FaultReported | sector has been declared as a fault on chain
| FaultedFinal | fault declared on chain
| Terminating | /
| TerminateWait | /
| TerminateFinality | /
| Removing | /
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
| SnapDealsDealsExpired | /
| SnapDealsRecoverDealIDs | /
| AbortUpgrade | /
| ReceiveSector | for external import

## Sealing pipeline - sector states errors

These variables correspond to the errors and failed states

{{< alert icon="tip" >}}
You can use the "Any error", if you want to create an acceptance logic for any failed sector state, avoiding complex operations
{{< /alert >}}

| Value | Description
| --- | --- | --- |
| Any error | Sum of all sector states in error
| AddPieceFailed | /
| CommitFinalizeFailed | /
| SealPreCommit1Failed | /
| SealPreCommit2Failed | /
| PreCommitFailed | /
| ComputeProofFailed | /
| RemoteCommitFailed | /
| CommitFailed | /
| PackingFailed | /
| FinalizeFailed | /
| TerminateFailed | /
| RemoveFailed | /
| SnapDealsAddPieceFailed | /
| ReplicaUpdateFailed | /
| ReleaseSectorKeyFailed | /
| FinalizeReplicaUpdateFailed | /

## Other variables

In addition to the variables related to the sealing pipeline, we also offers variables that are calculated at the moment when a proposal is received. 
These dynamic variables can be incorporated into each stages of an storage acceptance logic

| Value | Description | Unit
| --- | --- | --- |
| ReceivedOnTimeOfDayUTC | datetime utc at which the proposal is analyzed | Datetime
| ReceivedOnDayOfWeek | day of the week at which the proposal is analysed | Day of week

{{< alert icon="success" >}}
It's noteworthy that additional variables may become available in future versions of CIDgravity
{{< /alert >}}

