---
title: "Using Boost node"
description: "This guide describes the necessary steps to setup the CIDgravity connector with a Boost node."
lead: "This guide describes the necessary steps to setup the CIDgravity connector with a Boost node."
draft: false
images: []
menu:
    connector:
        parent: "connector-setup"
        identifier: "connector-setup-boost"
weight: 210
toc: true
---

# Requirements
1. Get a CIDgravity account : https://cidgravity.com
2. Set your get-ask prices to 0 and size to the widest range via the BoostUI:
    - Price          = 0
    - Verified Price = 0
    - Min Piece Size = 256
    - Max Piece Size = 32G or 64G
3. Install python modules : toml and requests
```
sudo apt install python3-toml python3-requests
```

# Get Started
1. Install the connector
```
sudo -i -u "<USER_RUNNING_BOOST_PROCESS>"
git clone https://github.com/CIDgravity/CIDgravity-X.git
cd CIDgravity-X
cp -n cidgravity_storage_connector.toml.sample cidgravity_storage_connector.toml
```
2. Add the CIDgravity authentication <TOKEN> (located at https://app.cidgravity.com under Settings/Other settings")
```
nano ./cidgravity_storage_connector.toml
```

## Configuration
    
1. Run the check process 
```
./cidgravity_storage_connector.py --check-boost
```

2. Enable "CIDgravity connector"
Add the following lines to boost config (usually ~/.boost/config.toml) under the [Dealmaking] and [LotusDealmaking] section
```
Filter = "<ABSOLUTE_PATH>/cidgravity_storage_connector.py --reject"
RetrievalFilter = "<ABSOLUTE_PATH>/cidgravity_storage_connector.py --reject"
```    
    
3. Restart boost
