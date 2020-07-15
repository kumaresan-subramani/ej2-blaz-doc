---
title: "Customize button with HTML element"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Customize button with HTML element

The uploader component allows you to customize the action buttons by using
[buttons](../../api/uploader/#buttons) &nbsp;property. Refer to the following example.

{% tab template="uploader/buttons", es5Template="button-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import {  Uploader } from '@syncfusion/ej2-inputs';
import { createElement } from '@syncfusion/ej2-base';

let uploadEle = createElement('span', { className: 'upload e-icons' });
uploadEle.innerHTML = 'Upload All';
let clearEle = createElement('span', { className: 'remove e-icons' });
clearEle.innerHTML = 'Clear All';

let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    autoUpload: false,
    buttons: {
      browse: 'Choose file',
      clear: clearEle,
      upload: uploadEle
    }
});
uploadObj.appendTo('#fileupload')
```

{% endtab %}