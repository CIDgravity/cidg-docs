---
title: "Manual import JSON"
description: "CIDgravity application is used to manage your settings, clients and pricing models acceptance rules"
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-manual-import-json"
weight: 104
toc: true
---

If you are more confortable with JSON format, we offer the possibility to edit and import a storage acceptance logic with this format

To access it, you must, when editing a storage acceptance logic, use the “JSON import” button.

![Acceptance JSON import for a storage acceptance logic](access-json-import-acceptance-logic.png)

A modal will open to display the JSON of the current logical acceptance loaded into the editor

![Modal JSON import for a storage acceptance logic](modal-json-import.png)

You can edit the JSON directly, copy it, paste a new one, and then refresh the editor by clicking the "Import" button

{{< alert icon="warning" >}}
Be careful with the names of the variables you use. If they are not respected, the import will not be possible
{{< /alert >}}