---
title: "Requirements"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
draft: false
images: []
menu:
    nextcloud:
        parent: "nextcloud-advanced-users"
        identifier: "nextcloud-advanced-users-requirements"
weight: 101
toc: true
---

This guide provides a structured, comprehensive walkthrough for setting up, configuring, and utilizing Nextcloud with Filecoin. It includes **file offloading**, **metadata access**, and **data retrieval** from Filecoin with examples for NodeJS, Go, Python, and Rclone.

This documentation corresponds to the "Starter" Offer. To unlock advanced features such as:

- Using your own Filecoin address
- Custom onboarding strategy
- Advanced onboarding dashboards

You will need a dedicated gateway and subscribe at least to the Pro Tier. 

For more information on these advanced features and pricing, visit [CIDgravity Pricing](https://www.cidgravity.com/pricing).

Before starting, ensure the following prerequisites are met:

1. Create an account by [reading this documentation]({{< ref "nextcloud/get-started/create-account/index.md" >}})
2. Understanding what is a CID on Filecoin by [reading this documentation]({{< ref "nextcloud/get-started/requirements/index.md#understand-what-is-a-cid" >}})
3. Follow the documentation below to get the WebDAV URL

## Get the WebDAV URL for your account:
The WebDAV URL allows you to connect any apps to the Nextcloud instance.
The format is similar to

```
https://nextcloud.twinquasar.io/remote.php/dav/files/<username>/
```

{{< video src="get-webdav-url.mp4" attributes="controls" width="960" >}}