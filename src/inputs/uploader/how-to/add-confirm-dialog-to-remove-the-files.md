---
title: "Add confirm dialog to remove the files"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Add confirm dialog to remove the files

You can customize the uploader component using confirm dialog before removing the files.
Here, ej2 dialog is used as confirm dialog. Refer to the following example.

{% tab template="uploader/confirm-dialog", es5Template="confirm-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader, FileInfo } from '@syncfusion/ej2-inputs';
import {createElement} from '@syncfusion/ej2-base';
import { Dialog } from '@syncfusion/ej2-popups';

let removeFile: FileInfo[];

let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    removing: onremove

});
uploadObj.appendTo('#fileupload');

// Initialize Dialog component
let dialog: Dialog = new Dialog({
    content: 'Are you sure want to remove the file?',
    buttons: [{'click': () => { onClick() }, buttonModel: { content: 'OK', cssClass: 'e-flat', isPrimary: true }},
        {'click': () => {dialog.hide(); }, buttonModel: { content: 'Cancel', cssClass: 'e-flat'} }],
    width: '250px',
    visible: false,
    target: '#container'
});
dialog.appendTo('#dialog');

function onClick() {
  dialog.hide();
  uploadObj.remove(removeFile[0], false, true);
}

function onremove(args: any) {
  removeFile=[];
  args.cancel = true;
  removeFile.push(args.filesData);
  dialog.show();
}
```

{% endtab %}