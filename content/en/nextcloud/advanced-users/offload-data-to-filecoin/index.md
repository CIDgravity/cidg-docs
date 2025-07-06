---
title: "Offload data to Filecoin"
description: "CIDgravity can be easily setup with Nextcloud to store your files on IPFS"
draft: false
images: []
menu:
  nextcloud:
    parent: "nextcloud-advanced-users"
    identifier: "nextcloud-advanced-users-offload-data-to-filecoin"
weight: 102
toc: true
---

Once everything is configured, you can start offloading files to Filecoin using various methods. This includes tools such as Web Interface, Nextcloud apps, or programmatically using Rclone, Node.js, Golang, or Python.


## Using the Nextcloud Web Interface

The simplest way to upload files is via the **Nextcloud WebUI**. Just drag and drop your file.

{{< img src="drop-file.jpg" alt="Upload a File with Nextcloud" >}}


## Using Nextcloud apps

Nextcloud provides native apps that support file synchronization and upload across platforms:

* 📱 **iOS / Android**
* 💻 **macOS / Windows / Linux**

🔗 [Download Nextcloud Apps](https://nextcloud.com/files/)


## Using Windows file explorer

Windows supports WebDAV natively through the "Map Network Drive" feature.

1. Open **File Explorer** → Right-click **This PC** → Choose **Map Network Drive**
2. Use the following URL:

   ```
   https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_USERNAME>/
   ```
3. Authenticate with your Nextcloud credentials.
4. Upload files into `/Public Filecoin`.


## Using macOS Finder

1. Open **Finder**
2. Press `Cmd + K` to open the **Connect to Server** window
3. Enter:

   ```
   https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_USERNAME>
   ```
4. Authenticate with your credentials
5. Drag files into `/Public Filecoin`

{{< video src="macos-native.mp4" attributes="controls" width="960" >}}


## Using Rclone

[Rclone](https://rclone.org/) is a versatile tool for syncing and managing remote storage.

### Install

```bash
curl https://rclone.org/install.sh | sudo bash
```

### Configure

```bash
rclone config
```

* Choose `n` for **New remote**
* Name: `cidgravity`
* Type: `WebDAV`
* URL: `https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_USERNAME>`
* Vendor: `Nextcloud`
* Username & password: your Nextcloud credentials
* Advanced config: `n`
* Confirm config: `y`
* Quit: `q`

### List folders

```bash
rclone lsd cidgravity:
```

### Sync a local folder to Filecoin

```bash
rclone sync /local/path "cidgravity:/Public Filecoin/"
```

### Mount the directory

```bash
rclone mount "cidgravity:/Public Filecoin/" /mnt/filecoin --vfs-cache-mode writes &
```


## Using Node.js

```javascript
import * as webdav from "webdav";
import fs from "fs";

const client = webdav.createClient(
  "https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_USERNAME>/",
  {
    username: "<YOUR_USERNAME>",
    password: "<YOUR_PASSWORD>",
  }
);

async function uploadFile() {
  const fileData = fs.readFileSync("<LOCAL_FILE_PATH>");
  await client.putFileContents("/Public Filecoin/file.txt", fileData);
  console.log("Upload successful!");
}
uploadFile();
```


## Using Golang

```go
package main

import (
    "bytes"
    "log"
    "net/http"
    "os"
)

func main() {
    username := "<YOUR_USERNAME>"
    password := "<YOUR_PASSWORD>"
    url := "https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_USERNAME>/Public Filecoin/file.txt"

    data, err := os.ReadFile("<LOCAL_FILE_PATH>")
    if err != nil {
        log.Fatal(err)
    }

    req, _ := http.NewRequest("PUT", url, bytes.NewReader(data))
    req.SetBasicAuth(username, password)

    resp, err := http.DefaultClient.Do(req)
    if err != nil || (resp.StatusCode != 201 && resp.StatusCode != 204) {
        log.Fatalf("Upload failed: %v", resp.Status)
    }

    log.Println("Upload successful!")
}
```


## Using Python

```python
from webdav3.client import Client

options = {
    'webdav_hostname': "https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_USERNAME>/Public Filecoin/",
    'webdav_login': "<YOUR_USERNAME>",
    'webdav_password': "<YOUR_PASSWORD>"
}

client = Client(options)
client.upload_sync(remote_path="/file.txt", local_path="<LOCAL_FILE_PATH>")
```


## Using any WebDAV compatible app

You can also offload files using any third-party app that supports WebDAV.

📚 Explore compatible apps:
👉 [WebDAV on Wikipedia](https://en.wikipedia.org/wiki/WebDAV)