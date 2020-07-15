---
title: "Trigger click event of input file from external button"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Trigger click event of input file from external button

Click event of input file from the external button can be triggered using the `click` event of button.
In the following sample, you can find the triggered click event of input file from `Essential JavaScript 2 Button`.

{% tab template="uploader/external-click", es5Template="click-event", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

//Initialize the control by preload files
let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
});
uploadObj.appendTo('#fileupload');

document.getElementById('browse').onclick = () => {
    document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
};

```

{% endtab %}