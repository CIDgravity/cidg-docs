---
title: "Claim a miner"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "This guide describes how you start using CIDgravity with a first miner."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-get-started"
        identifier: "storage-providers-get-started-claim-a-miner"
weight: 101
toc: true
---

Get ready onboarding deals with CIDgravity in less than 5 min. All you need is a valid github account and being able to prove the miner ownership by signing a challenge (remote access to the miner)

Connect to the [CIDgravity app](https://app.cidgravity.com) and follow the onboarding instructions. This will guide you through the the few steps to setup the initial configuration. 

## Compatibility matrix

|Node           |Supported|
|---------------|---------|
|boost          | ✅      |
|droplet(venus) | ✅      |
|lotus-markets  | ❌      |

## Fill the miner ID

Enter the minerID you wish to use to start the claiming process.

{{< img src="enter-a-miner-id.png" alt="Enter the minerID you want to claim" >}}

In the next step, you will need to sign a challenge message with the worker key to confirm miner ownership.

The command is generated with all required information as follows:

```shell
lotus wallet sign [WORKER_ADDRESS] [ONETIME_CHALLENGE]
```

## Define a friendly name

The friendly name is utilized throughout the entire app for easy identification of a miner.
It can be modified later through the ```settings```.

{{< alert icon="warning" >}}
The friendly name is attached to the miner and will remain consistent across all users who claim this miner.
changing this name will reflect to every users.
{{< /alert >}}

{{< img src="define-friendly-name.png" alt="Choose a friendly name for this miner" >}}

{{< alert icon="success" >}}
If the miner already exists in CIDgravity (previously successfully claimed by you or someone else), the claiming process is ending here.
We recommend to verify the miner connectivity by running an end to end connectivity check :  ```Help Center``` / ```Diagnosis```
{{< /alert >}}

## Import settings from another miner (optional)

If you already manage another miner with CIDgravity, you can directly import its settings.

## Initial settings (optional)

- **Number of storage deals per hour**: The maximum number of storage deals accepted over the last 60 minutes, across all clients.
- **Cumulative storage deal size per hour**: The maximum cumulative storage deal size (GiB) accepted over the last 60 minutes.
- **Retrieval deals per hour**: The maximum number of graphsync retrieval deals accepted over the last 60 minutes, across all clients.
- **Custom message**: A personalized message that will be appended to rejection message sent to clients (e.g. "you can contact us at me@mydomain.wyz")
- **Accept storage deals from unknown clients**: Enable or disable the storage deals from clients not previously created. If disabled, such deals will be rejected, ensuring that only recognized clients data are stored.

{{< img src="set-global-limits.png" alt="Define the global limits for this miner" >}}

## Connector token

The last screen presents the token needed to configure the CIDgravity connector on the miner.
This token is also accessible from the ```Settings``` page.

{{< alert icon="tip" >}}
You will have the option to initiate an end-to-end connectivity test once the connector is configured.
{{< /alert >}}
