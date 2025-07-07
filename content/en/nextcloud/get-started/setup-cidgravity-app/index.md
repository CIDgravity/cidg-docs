---
title: "Setup CIDgravity app"
description: "Connect CIDgravity to your Nextcloud instance and start storing files on IPFS."
lead: "The CIDgravity app is the component allowing your Nextcloud instance to talk to Filecoin."
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-get-started"
    identifier: "nextcloud-get-started-setup-cidgravity-app"
weight: 104
toc: true
---

## Enable external storage support

This is a mandatory component required for the CIDgravity app to work properly.

Go on the available apps page by clicking the **grid icon** at the top right of the dashboard. 

<img src="img/install_09.png" alt="Apps menu" width="640">
<br /><br />

On the left-hand side, select **Disabled apps** to find core features that are not yet active in your installation. 

<img src="img/install_10.png" alt="Disabled apps section" width="640">
<br /><br />

Locate the **External Storage Support** app and click **Enable**. 

<img src="img/install_11.png" alt="Enable external storage support" width="640">
<br /><br />

## Enable the CIDgravity app

The app can be directly installed from the Nextcloud app store.

Use the **search bar** in the top right to look for the CIDgravity app. This step helps you quickly locate the integration needed for IPFS support. 

<img src="img/install_13.png" alt="Search for CIDgravity" width="640">
<br /><br />

Once you've found **CIDgravity – IPFS/Filecoin External Storage**, click **Download and Enable** to install it on your Nextcloud instance. 

<img src="img/install_14.png" alt="Install CIDgravity app" width="640">


## Connect the CIDgravity app

To configure the new storage, open the **Administration Settings** by clicking your user icon in the top-right menu and selecting **Settings**. 

<img src="img/install_15.png" alt="Admin settings" width="640">
<br /><br />

In the sidebar, find the **External Storage** section under **Administration** to set up your IPFS backend. 

<img src="img/install_16.png" alt="External storage settings" width="640">
<br /><br />

Create a new storage entry by entering a folder name (e.g., `IPFS Vault`), and provide your credentials from [https://nextcloud.twinquasar.io](https://nextcloud.twinquasar.io). You can also check **All users** if you want others to access it.

Click the ✅ checkmark to save the configuration. 

<img src="img/install_17.png" alt="Enter IPFS credentials" width="640">
<br /><br />

For security reasons, Nextcloud will ask you to confirm your admin password before applying any changes to the storage configuration. 

<img src="img/install_18.png" alt="Confirm with password" width="640">
<br /><br />

If everything is correctly configured, you’ll see a green checkmark or arrow next to the storage entry. This confirms the IPFS storage is active and accessible. 

<img src="img/install_19.png" alt="Green arrow success" width="640">