---
title: "Setup CIDgravity connector"
description: "This guide outlines the essential steps required to configure the CIDgravity connector in conjunction with a Boost node."
lead: "To communicate with CIDgravity, a connector needs to be deployed on the miner markert node (boost / dropplet)."
draft: false
images: []
menu:
    storage-providers:
        parent: "storage-providers-get-started"
        identifier: "storage-providers-get-started-connector"
weight: 102
toc: true
---

The CIDgravity connector is an unprivileged open source python script. It leverage the standard dealFilter hooks, called on each deal request.

It does NOT require to open any ports, access to any Filecoin keys, nor run as a deamon. Its lightweight with an average decision taken in less than 2s (Boost expects the decision to be taken within 30sec).

Jump here [https://github.com/CIDgravity/CIDgravity-X]  and follow the instructions.
