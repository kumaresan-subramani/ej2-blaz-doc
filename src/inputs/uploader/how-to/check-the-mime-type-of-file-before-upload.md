---
title: "Check the MIME type of file before upload"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Check the MIME type of file before upload

By using the [uploading](../../api/uploader/#uploading) event, you can get the file MIME type before uploading it to the server.
In the following sample, file MIME type is shown in the alert box before the file starts to upload.

{% tab template="uploader/mime-type", es5Template="mime", sourceFiles="app.ts,index.html" %}

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
    // get the file MIME type
    alert("File MIME type is: " + args.fileData.rawFile.type)
}

```

{% endtab %}