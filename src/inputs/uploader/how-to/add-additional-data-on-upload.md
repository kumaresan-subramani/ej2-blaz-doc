---
title: "Add additional data on upload"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Add additional data on upload

The uploader component allows you to add additional data on file upload, which is used to get in the server-side.
By using [uploading](../../api/uploader/#uploading) event and its customFormData argument, you can achieve this behavior. Refer to the following example.

In the following code snippet, explains about how to add additional data on file upload.

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';


let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    uploading: onFileUpload

});
uploadObj.appendTo('#fileupload');

function onFileUpload(args: any) {
    // add addition data as key-value pair.
    args.customFormData = [{'name': 'Syncfusion INC'}];
}
```

## Server side for adding additional data

```csharp
    // Get the additional data in server end by corresponding key.
    var data = HttpContext.Current.Request.Form["name"];
```