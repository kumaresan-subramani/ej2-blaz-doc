---
title: "Getting Started"
component: "Uploader"
description: "Explains to get started with HTML5 file upload control with its key features such as asynchronous mode, handle success, fail action, etc."
---

# Getting Started

This section explains how to create and configure the simple uploader component.

## Dependencies

The following are the dependencies required to use the uploader component in your application:

```js
|-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons

```

## Set up of the development environment

To get started with the uploader component, you have to clone the Essential JS 2 [`quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and install the npm packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common
settings (`src/styles/styles.css`, `system.config.js` ) to start
all the Essential JS 2 components.

## Initialize the uploader

The uploader can be initialized through input tag. Add the HTML input element that needs to be initialized as a uploader in `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 Uploader component</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <div id='container' style="margin:0 auto; width:300px;">
        <!--element which is going to render the Uploader-->
        <input type="file" id='fileupload' />
    </div>

</body>

</html>
```

> The [Custom Resource Generator (CRG)](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific components.
> This web tool is useful to combine the required component scripts and styles in a single file.

Now, import the  uploader component to your `app.ts` and initialize it to the element `#fileupload` as follows.

`[src/app/app.ts]`

```typescript

// initialize Uploader component
var uploadObject = new ej.inputs.Uploader();
// render initialized Uploader
uploadObject.appendTo('#fileupload');

```

## Run the application

After completing the configuration to render the basic uploader, run the following command to display
the output in your default browser.

```cmd
npm run start
```

> From v16.2.41 version, the `Essential JS2 AJAX` library has been integrated for uploader server requests.
Hence, use the third party `promise` library like blue-bird to use the uploader in Internet Explorer.

The following example illustrates the output in your browser.

{% tab template="uploader/getting-started", es5Template="getting-template", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    // disable the auto upload functionalities
    autoUpload: false
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Adding drop area

By default, the uploader component allows to upload files by drag the files from file explorer, and drop into the drop area.  You can configure any other external element as drop target using [dropArea](../api/uploader/#droparea) property.

In the following sample, drop target is configured.

{% tab template="uploader/drop-area", es5Template="droparea-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    autoUpload: false,
    dropArea: document.getElementById('droparea')
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Configure asynchronous settings

The uploader component process the files to upload in Asynchronous mode by default. Define the properties [saveUrl](../api/uploader/asyncSettingsModel/#saveurl) and [removeUrl](../api/uploader/asyncSettingsModel/#removeurl) to handle the save and remove action as follows.

{% tab template="uploader/async-settings", es5Template="async-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
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

## Handle success and failed upload

You can handle the success and failure actions using the [success](../api/uploader/#success) and [failure](../api/uploader/#failure) &nbsp;events. To handle these event, define the function and assign it to corresponding event as follows.

{% tab template="uploader/success_failed", es5Template="sucfail-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    success: onUploadSuccess,
    failure: onUploadFailure
});
// render initialized Uploader
uploadObject.appendTo('#fileupload');

function onUploadSuccess(args: any): void  {
  if (args.operation === 'upload') {
    console.log('File uploaded successfully');
  }
}
function onUploadFailure(args: any): void  {
  console.log('File failed to upload');
}
```

{% endtab %}

## See Also

* [How to add additional data on upload](./how-to/add-additional-data-on-upload)
* [Achieve file upload programmatically](./how-to/achieve-file-upload-programmatically)
* [Achieve invisible upload](./how-to/achieve-invisible-upload)
