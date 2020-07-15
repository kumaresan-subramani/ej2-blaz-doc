---
title: "Check file size before uploading"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Check file size before uploading

By using the [uploading](../../api/uploader/#uploading) event, you can get the file size before uploading it to the server.
File object contains the file size in bytes only.
You can convert the size to standard formats (`KB` or `MB`) using [bytesToSize](../../api/uploader/#bytestosize) method.

{% tab template="uploader/check-file-size", es5Template="file-size", sourceFiles="app.ts,index.html,index.css" %}

```typescript

import { Uploader } from '@syncfusion/ej2-inputs';

//Initialize the control by preload files
let uploadObj: Uploader = new Uploader({
    autoUpload: false,
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    uploading: onBeforeUpload
});
uploadObj.appendTo('#fileupload');

function onBeforeUpload(args): void {
    // get the file size in bytes
    let sizeInBytes: number = args.fileData.size;
    // get the file size in standard format
    alert("File size is: " + uploadObj.bytesToSize(sizeInBytes));
}

```

{% endtab %}