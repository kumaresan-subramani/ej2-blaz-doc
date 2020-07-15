---
title: "Customize progressbar"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Customize progressbar

You can customize the progress bar’s size, color, and background by overriding  the styles in uploader component.
Refer to the following example.

{% tab template="uploader/progress-customize", es5Template="progress-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    }
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}