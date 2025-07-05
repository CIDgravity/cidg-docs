---
title: "Install and configure the app"
description: "Connect CIDgravity to your Nextcloud instance and start storing files on IPFS."
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-get-started"
    identifier: "nextcloud-get-started-install-and-setup-application"
weight: 103
toc: true
---

### Create an Admin Account

Start by setting up your admin credentials. Choose a secure username and password, then click **Install** to complete the initial setup of your Nextcloud server. 

<img src="img/install_07.png" alt="Create admin account" width="640">

### Skip Recommended Apps

Nextcloud will suggest installing additional apps. These are optional and not required for CIDgravity, so you can safely click **Skip** to proceed. 

<img src="img/install_08.png" alt="Skip recommended apps" width="640">

### Open the Apps Menu

After setup, access the list of available apps by clicking the **grid icon** at the top right of the dashboard. 

<img src="img/install_09.png" alt="Apps menu" width="640">

### Go to Disabled Apps

On the left-hand side, select **Disabled apps** to find core features that are not yet active in your installation. 

<img src="img/install_10.png" alt="Disabled apps section" width="640">

### Enable External Storage Support

Locate the **External Storage Support** app and click **Enable**. This app is essential for integrating external file systems like IPFS. 

<img src="img/install_11.png" alt="Enable external storage support" width="640">

### Search for CIDgravity

Use the **search bar** in the top right to look for the CIDgravity app. This step helps you quickly locate the integration needed for IPFS support. 

<img src="img/install_13.png" alt="Search for CIDgravity" width="640">

### Install CIDgravity

Once you've found **CIDgravity – IPFS/Filecoin External Storage**, click **Download and Enable** to install it on your Nextcloud instance. 

<img src="img/install_14.png" alt="Install CIDgravity app" width="640">

### Open Administration Settings

To configure the new storage, open the **Administration Settings** by clicking your user icon in the top-right menu and selecting **Settings**. 

<img src="img/install_15.png" alt="Admin settings" width="640">

### Go to External Storage

In the settings sidebar, find the **External Storage** section under **Administration** to set up your IPFS backend. 

<img src="img/install_16.png" alt="External storage settings" width="640">

### Add Your IPFS Storage Details

Create a new storage entry by entering a folder name (e.g., `IPFS Vault`), and provide your credentials from [https://nextcloud.twinquasar.io](https://nextcloud.twinquasar.io). You can also check **All users** if you want others to access it.

Click the ✅ checkmark to save the configuration. 

<img src="img/install_17.png" alt="Enter IPFS credentials" width="640">

### Confirm with Your Account Password

For security reasons, Nextcloud will ask you to confirm your admin password before applying any changes to the storage configuration. 

<img src="img/install_18.png" alt="Confirm with password" width="640">

### Check for the Green Arrow

If everything is correctly configured, you’ll see a green checkmark or arrow next to the storage entry. This confirms the IPFS storage is active and accessible. 

<img src="img/install_19.png" alt="Green arrow success" width="640">
