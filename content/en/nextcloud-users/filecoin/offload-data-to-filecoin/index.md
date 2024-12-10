---
title: "Offload data to Filecoin"
description: "CIDgravity application serves as a comprehensive tool for managing and monitoring of : clients, pricing, acceptance criterias, avalability and activity."
lead: "You can offload your files to Filecoin through various methods. Below are the supported options"
draft: false
images: []
menu:
    nextcloud-users:
        parent: "nextcloud-users-filecoin"
        identifier: "nextcloud-users-filecoin-offload"
weight: 202
toc: true
---

### With Nextcloud WebUI

You can simply use the **Nextcloud Web Interface** to **drag and drop files** into the UI for offloading to Filecoin.

{{< img src="drop-file.jpg" alt="Upload a File with Nextcloud" >}}

### With Nextcloud Apps

You can use the **Nextcloud mobile or desktop applications** across multiple platforms to handle file uploads. Supported platforms:

- **iOS**
- **Android**
- **macOS**
- **Windows**
- **Linux**

For more details, visit the [Nextcloud](https://nextcloud.com/files/).

### With Windows Native

You can use Windows' built-in WebDAV feature to map and upload.

#### Instructions:

1.  Map the WebDAV directory using the **Map Network Drive** feature.
    URL Example:

```
https://nextcloud.twinquasar.io/remote.php/dav/files/<username>/
```

2.  Drag and drop files into the "/Public Filecoin" directory to store them on Filecoin.

### With MacOS Native

Use Finder's native WebDAV integration

#### Instructions:

1.  Open Finder.
2.  Press `Cmd + K`.
3.  Enter the WebDAV URL:

```
https://nextcloud.twinquasar.io/remote.php/dav/files/<username>
```

4.  Authenticate with your credentials.
5.  Drag and drop files into the "/Public Filecoin" directory to store them on Filecoin.

{{< video src="macos-native.mp4" attributes="controls" width="960" >}}

### With Rclone Sync

**Rclone** is a powerful command-line tool for syncing, transferring, and mounting files across cloud storage services like S3, WebDAV (including Nextcloud), and local storage. For more information, visit the [official documentation](https://rclone.org/).

#### Installation:

```bash
curl https://rclone.org/install.sh | sudo bash
```

#### Configure Rclone

```bash
rclone config
choose "n"  for "New remote"
choose name for remote --> cidgravity
choose "Type of Storage" --> Webdav
provide URL for webdav access --> https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>
choose Vendor --> Nextcloud
specify "user" --> <YOUR_NEXTCLOUD_USERNAME>
password --> y (Yes type in my own password)
specify "password" --> <YOUR_NEXTCLOUD_PASSWORD>.
bearer token --> ""
Edit advanced config? --> n (No)
Remote config --> y (Yes this is OK)
Current remotes --> q (Quit config)
```

#### Check configuration

```bash
rclone lsd  cidgravity:
          -1 2024-12-07 10:53:21        -1 Public Filecoin
```

#### Sync Example:

```bash
rclone sync /local/path/to/files "cidgravity:/Public Filecoin/"
```

Mount Example:

```bash
rclone mount "cidgravity:/Public Filecoin/" /mnt/filecoin --vfs-cache-mode writes &
```

### With Node.JS

```javascript
import * as webdav from "webdav";
import fs from "fs";
// Configure your Nextcloud WebDAV URL and credentials
const client = webdav.createClient(
  "https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>/",
  {
    username: "<YOUR_NEXTCLOUD_USERNAME>",
    password: "<YOUR_NEXTCLOUD_PASSWORD>",
   }
);

async function uploadFile() {
  try {
    const filePath = "<PATH_OF_LOCAL_FILE_TO_UPLOAD>";
    const destinationPath = "/Public Filecoin/file.txt";

    // Read the file data
    const fileData = fs.readFileSync(filePath);

    // Use `client.putFileContents()` to upload the file
    await client.putFileContents(destinationPath, fileData);

    console.log("Upload successful!");
  } catch (error) {
    console.error("Error uploading file:", error);
  }
}

uploadFile();
```

### With Golang

```go
package main

import (
    "bytes"
    "log"
    "net/http"
    "os"
)

func main() {
    username := "<YOUR_NEXTCLOUD_USERNAME>"
    webDAVURL := "https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>/Public Filecoin/file.txt"
    password := "<YOUR_NEXTCLOUD_PASSWORD>"
    filePath := "<PATH_OF_LOCAL_FILE_TO_UPLOAD>"

    fileData, err := os.ReadFile(filePath)
    if err != nil {
        log.Fatalf("Error reading file: %v", err)
    }

    req, err := http.NewRequest("PUT", webDAVURL, bytes.NewReader(fileData))
    if err != nil {
        log.Fatalf("Error creating request: %v", err)
    }
    req.SetBasicAuth(username, password)

    resp, err := http.DefaultClient.Do(req)
    if err != nil {
        log.Fatalf("Error making request: %v", err)
    }
    defer resp.Body.Close()

    if resp.StatusCode == http.StatusCreated || resp.StatusCode == http.StatusNoContent {
        log.Println("File uploaded successfully!")
    } else {
        log.Fatalf("Upload failed with status: %s", resp.Status)
    }
}
```

### With Python 3

```python
from webdav3.client import Client

# WebDAV configuration
options = {
    'webdav_hostname': "https://nextcloud.twinquasar.io/remote.php/dav/files/<YOUR_NEXTCLOUD_USERNAME>/Public Filecoin/",
    'webdav_login': "<YOUR_NEXTCLOUD_USERNAME>",
    'webdav_password': "<YOUR_NEXTCLOUD_PASSWORD>"
}

# Initialize the WebDAV client
client = Client(options)

# Define file paths
local_file_path = "<PATH_OF_LOCAL_FILE_TO_UPLOAD>"  # Replace with your local file path
remote_file_path = "/file.txt"  # Destination on the WebDAV server

# Upload the file
try:
    client.upload_sync(remote_path=remote_file_path, local_path=local_file_path)
    print("File uploaded successfully!")
except Exception as e:
    print(f"Error during upload: {e}")
```
### With Any WebDAV compatible App

You can utilize hundreds of third-party applications that support **WebDAV** for file offloading. Examples include popular WebDAV-compatible tools. Reference the [WebDAV Resource List](https://en.wikipedia.org/wiki/WebDAV) for supported applications.

