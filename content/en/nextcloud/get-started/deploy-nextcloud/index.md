---
title: "Deploy Nextcloud"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
lead: "CIDgravity is designed to be added to your personal or organization-managed Nextcloud instance."
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-get-started"
    identifier: "nextcloud-get-started-deploy-nextcloud"
weight: 102
toc: true
---


## Requirements

* **Nextcloud version**: **29 or higher**
* **PHP**: 8.2 or 8.3
* **Database**: MariaDB, MySQL, or PostgreSQL
* **Web server**: Apache or Nginx
* **OS**: Linux (Debian, Ubuntu, RHEL, etc.)

> Make sure your server meets the [official system requirements](https://docs.nextcloud.com/server/29/admin_manual/installation/system_requirements.html) before proceeding.


## Installation Methods

You can install Nextcloud using any of the following supported methods

### Manual Installation (Linux)

Set up Nextcloud on a traditional LAMP or LEMP stack.
- [Linux install guide (official)](https://docs.nextcloud.com/server/29/admin_manual/installation/source_installation.html)

### Docker

Easiest method to spin up a full Nextcloud environment with minimal setup.
- [Docker AIO setup](https://github.com/nextcloud/all-in-one)

### Snap Package

Quick install with auto-configuration and updates.
- [Snap install instructions](https://snapcraft.io/nextcloud)