---
title: "Get the total size of selected files"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Get the total size of selected files

You can get the total size of selected files before uploading it to the designated server. This can be achieved by using the selected event. Refer to the following example to calculate the total file size.

{% tab template="uploader/file-size", es5Template="size-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import {  Uploader, FileInfo, SelectedEventArgs } from '@syncfusion/ej2-inputs';
import { Event } from '@syncfusion/ej2-base';

let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    selected: onSelect

});
uploadObj.appendTo('#fileupload')

function onSelect(args: SelectedEventArgs): void {
    let totalSize: number = 0;
    for (let file of args.filesData) {
        totalSize = totalSize + file.size;
    }
    let size: string = uploadObj.bytesToSize(totalSize);
    alert("Total select file's size is " + size);
}
```

{% endtab %}