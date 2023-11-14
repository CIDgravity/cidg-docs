---
title: "Setup Venus connector"
description: "This guide outlines the essential steps required to configure the CIDgravity connector in conjunction with a Droplet node."
lead: "This guide outlines the essential steps required to configure the CIDgravity connector in conjunction with a Droplet node."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-get-started"
        identifier: "storage-providers-get-started-venus"
weight: 103
toc: true
---

# Requirements

Here are the steps you need to follow:

1. Obtain a CIDgravity account by visiting [https://cidgravity.com](https://cidgravity.com)
<br /><br />

2. Set your get-ask prices to 0 and size to the widest range via the Droplet Settings :
    - Price          = 0
    - Verified Price = 0
    - Min Piece Size = 256
    - Max Piece Size = 32G or 64G
<br /><br />

3. Install the required Python modules `toml` and `requests` using the following command 

```
sudo apt install python3-toml python3-requests
```

# Get Started

1. Install the connector and create the necessary configuration file using

```
sudo -i -u "<USER_RUNNING_DROPLET_PROCESS>"
git clone https://github.com/CIDgravity/CIDgravity-X.git
cd CIDgravity-X
cp -n cidgravity_storage_connector.toml.sample cidgravity_storage_connector.toml
```

2. Add the CIDgravity authentication <TOKEN> (located at https://app.cidgravity.com under `Settings`)

```
nano ./cidgravity_storage_connector.toml
```

## Configuration

1. Run the check process 

```
./cidgravity_storage_connector.py --check-venus  
```

2. Enable "CIDgravity connector"

Add the following lines to Droplet config (under path `~/.droplet/config.toml` by default) in the [CommonProvider] section (for more details, please refer to documentation [here](https://github.com/ipfs-force-community/droplet/blob/master/docs/en/droplet-configurations.md))

```
Filter = "<ABSOLUTE_PATH>/cidgravity_storage_connector.py --reject"
RetrievalFilter = "<ABSOLUTE_PATH>/cidgravity_storage_connector.py --reject"
```

3. Restart Droplet