---
title: "Storage acceptance logic"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "Control deal acceptance based on the realtime state of the sealing pipeline"
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-manage"
        identifier: "storage-providers-manage-acceptance-logic"
weight: 202
toc: true
---

Access: `Storage` > `Acceptance logic`

{{< alert icon="warning" >}}
This feature only works for ONLINE deals and requires Boost >= 2.1.0
{{< /alert >}}

With Acceptance logic the miner can be configured to accept deals based on simple, combined or computed states of sectors in the sealing pipeline but also time of the day, Filecoin price, etc....

## Definition

A storage acceptance logic is a rule-based system for the determination of transaction approval or rejection, based on diverse criterias, such as:

- Sealing Pipeline State
- Temporal factors, like the time of day or day of the wee
- FIL price (to be introduced in the near future)
- Concurrent Download Thresholds (to be introduced in the near future)

Acceptance logic is the last component of the CIDgravity acceptance process, it occurs after the pricing validation (for more information on how proposals are processed : [reference]({{< ref "reference/storage-deal-processing/index.md" >}}).

Like a pricing model, an acceptance logic can be :
- attached to clients
- defined as default and apply to storage proposal from unregistered clients or for clients without acceptance logic defined.

## How it works

CIDgravity implements [JSON-formatted logic](https://jsonlogic.com/). 

Here is an illustrative example of a CIDgravity JSON logic:

```json
{
   "or":[
      {
         ">=":[
            {
               "var":"PreCommit1"
            },
            10
         ]
      },
      {
         "<=":[
            {
               "var":"PreCommit2"
            },
            2
         ]
      }
   ]
}
```

The storage acceptance logic accommodates the following components:
- `Variables`: sector state, date, etc...
- `Values`: integer, time, day of the week
- `Advanced operations`: +, -, *, /
- `Comparison signs`: >, <, =, any, contains, etc...

### Variables

#### Sealing pipeline - sector states

These variables correspond to the states within the sealing pipeline, excluding errors or failed states

{{< alert icon="tip" >}}
Theses variables are expressed in number of sectors, represented as an integer.
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

#### Sealing pipeline - sector states errors

These variables correspond to the errors and failed states

{{< alert icon="tip" >}}
"Any error" is an aggregate of all sectors in error, helpful for simplifying acceptance logics
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

#### Other variables

CIDgravity also offers variables that are calculated when a proposal is received. 
These dynamic variables can be incorporated into each stages

| Value | Description | Unit
| --- | --- | --- |
| ReceivedOnTimeOfDayUTC | datetime utc at which the proposal is analyzed | Datetime
| ReceivedOnDayOfWeek | day of the week at which the proposal is analysed | Day of week

{{< alert icon="success" >}}
Additional variables may become available in future versions of CIDgravity
{{< /alert >}}

### Available values

Values are filled when creating a JSoN logic. The value type is enforced by the JSON logic editor (integer, date, time, etc...)

### Supported Comparison signs

- `==`
- `<=`
- `>=`
- `>`
- `<`
- `!=`
- `Between`
- `Not between`
- `Is null`
- `Is not null`

{{< alert icon="tip" >}}
With these comparison operators, you can compare values, variables (e.g., VariableA < VariableB), or even operations (e.g., VariableA + VariableB !== VariableC)
{{< /alert >}}

### Advanced operations

The storage acceptances logic also supports operations between variables, enabling the combination of multiple variables to construct advanced logic that can fit a wide range of requirements.

Like: `(PC1 + AP) < 16`

#### Supported operations

- `Sum`
- `Substraction`
- `Multiplication`
- `Division`

{{< alert icon="warning" >}}
Each operation is limited to a maximum ofi 2 elements, but operations can be combined to cover more complex operations.
For example, to sum 3 elements : `VariableA + (VariableB + VariableC)`
{{< /alert >}}

#### Access advanced operations

Click on the ellipsis icon (`⋮`) and then select `Advanced operations` from the dropdown menu. 

This will open a menu where supported operations are available.

{{< img src="add-advanced-operations.png" alt="Add advanced operation to a storage acceptance logic rule" >}}

## Manual import from JSON

To facilitate manipulating, editing and sharing JSON logic, CIDgravity implements a `JSON import` button evailable when edition a JSON logic.

It allows to easily export to clipboard and import JSON logic.

{{< img src="access-json-import-acceptance-logic.png" alt="Acceptance JSON import for a storage acceptance logic" >}}

{{< img src="modal-json-import.png" alt="Modal JSON import for a storage acceptance logic" >}}

Edit the JSON, copy its contents, insert a new JSON structure, and subsequently update the editor by clicking the `Import` button.

{{< alert icon="warning" >}}
Import will fail if variable names are invalid (case sensitive).
{{< /alert >}}

## Manage existing logics

{{< img src="logics-list.png" alt="Manage storage acceptance logics using the management page" >}}

Each acceptance logic listed offers several options:

- View
- Edit
- Remove
- Set as default

{{< alert icon="tip" >}}
Claiming a new miner will automatically create sample acceptance logics, they can be used as it is, deleted, edited.
{{< /alert >}}

## Testing

Acceptance logic can be tested and troubleshooted from the [Playground]

To simulate a storage acceptance logic, [you can use the playground.]({{< ref "storage-providers/manage/playground/index.md" >}})
