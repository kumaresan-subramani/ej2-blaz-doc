---
title: "Validate image/* on drop"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Validate image/* on drop

The uploader component allows you to upload all type of images by setting
**image/* ** to [allowedExtensions](../../api/uploader/#allowedextensions) property.

By default, the behavior is working with select a file using browse button. But, this behavior doesn’t support
on drag and drop the files. You can handle this behavior manually using `selected` event by filtering the file types from application.

In the following example, validated image files using images/*. You are able to drag and drop the image files with extension of PNG, JPG, BPG, GIF and TIFF to upload it.

{% tab template="uploader/validate-image", es5Template="image-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';


let uploadObj: any = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    autoUpload: false,
    allowedExtensions: 'image/*',
    selected: onSelect

});
uploadObj.appendTo('#fileupload');

function onSelect(args: any): void {
  if (args.event.type === 'drop') {
    let allImages: Array<string> = ['png', 'jpg', 'jpeg', 'gif', 'tiff', 'bpg'];
    let files = args.filesData;
    let modifiedFiles = [];
    for (let file of files) {
      if (allImages.indexOf(file.type) === -1) {
        file.status = 'File type is not allowed';
        file.statusCode = '0';
      }
      modifiedFiles.push(file);
    }
    args.isModified = true;
    args.modifiedFilesData = modifiedFiles.concat(uploadObj.filesData);
  }
}
```

{% endtab %}