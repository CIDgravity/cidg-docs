---
title: "Manual import JSON"
description: "CIDgravity application serves as a comprehensive tool for managing settings, clients, and the acceptance rules of pricing models"
draft: false
images: []
menu:
    application:
        parent: "storage-acceptance-logic"
        identifier: "storage-acceptance-logic-manual-import-json"
weight: 104
toc: true
---

If you are more inclined towards JSON format, we provide the option to modify and import storage acceptance logic in this structure.

To access this feature, while editing a storage acceptance logic, simply utilize the `JSON import` button.

![Acceptance JSON import for a storage acceptance logic](access-json-import-acceptance-logic.png)

A modal window will be launched, presenting the JSON representation of the storage acceptance logic that is currently loaded in the editor.

![Modal JSON import for a storage acceptance logic](modal-json-import.png)

You have the ability to directly modify the JSON, copy its contents, insert a new JSON structure, and subsequently update the editor by clicking the `Import` button.

{{< alert icon="warning" >}}
Please exercise caution when using variable names. Failure to adhere to the specified naming conventions may result in import errors
{{< /alert >}}