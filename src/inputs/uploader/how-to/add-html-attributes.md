---
title: "Add html attributes"
component: "Uploader"
description: "This section describes how to add additional html attributes."
---

# Add html attributes

You can add the additional HTML attributes such as disabled, value, name, and more to the element using the [htmlAttributes](../api/uploader/#htmlAttributes) property. If you configured both the property and equivalent HTML attribute, then the component considers the property value.

The following example demonstrates how to set attributes in htmlAttributes property in the Uploader.

{% tab template="uploader/html-attr", es5Template="html-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript

import { Uploader } from '@syncfusion/ej2-inputs';

//Initialize the control by preload files
let uploadObj: Uploader = new Uploader({
    autoUpload: false,
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    htmlAttributes: {"disabled": "true"}
});
uploadObj.appendTo('#fileupload');

```

{% endtab %}