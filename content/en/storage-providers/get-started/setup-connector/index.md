---
title: "Setup CIDgravity connectivity"
description: "This guide outlines the essential steps required to configure CIDgravity in conjunction with the market node (Curio-market, boost, dropplet)."
lead: "To communicate with CIDgravity, a connector needs to be deployed on the miner markets node (boost / dropplet). Curio is natively integrating with CIDgravity, the CIDgravity connector is not needed."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-get-started"
        identifier: "storage-providers-get-started-connector"
weight: 102
toc: true
---

## For Curio

Only the CIDgravity token is needed to setup the connectivity

## For Boost and Dropplet

The CIDgravity connector is an unprivileged open source python script. It leverages the standard dealFilter hooks called on each deal request.

It does NOT require to open any ports, need access to any Filecoin keys, nor run as a deamon. Its lightweight with an average decision taken in less than 2s (Boost expects the decision to be taken within 30sec).

Jump [here](https://github.com/CIDgravity/CIDgravity-X) and follow the instructions.
