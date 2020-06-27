---
title: "Getting Started"
component: "DocumentEditor"
description: "Learn how to get started using JavaScript document editor component through simple steps."
---

# Getting Started

This section explains the steps to create a Word document editor within your application and demonstrates the basic usage of the DocumentEditor component.

## Dependencies

Following is the list of minimum dependencies required to use the documenteditor.

```javascript
|-- @syncfusion/ej2-documentEditor
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-charts
```

## Installation and configuration

To get started with DocumentEditor component, you can clone the [`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and install necessary packages by using the following commands.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

## Configuring system JS

[Syncfusion DocumentEditor packages](#dependencies/) have to be mapped in the `system.config.js` configuration file.

```javascript
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/',
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-file-utils": "syncfusion:ej2-file-utils/dist/ej2-file-utils.umd.min.js",
        "@syncfusion/ej2-compression": "syncfusion:ej2-compression/dist/ej2-compression.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-navigations": "syncfusion:ej2-navigations/dist/ej2-navigations.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-dropdowns": "syncfusion:ej2-dropdowns/dist/ej2-dropdowns.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-office-chart": "syncfusion:ej2-office-chart/dist/ej2-office-chart.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "@syncfusion/ej2-charts": "syncfusion:ej2-charts/dist/ej2-charts.umd.min.js",
        "@syncfusion/ej2-svg-base": "syncfusion:ej2-svg-base/dist/ej2-svg-base.umd.min.js",
        "@syncfusion/ej2-pdf-export": "syncfusion:ej2-pdf-export/dist/ej2-pdf-export.umd.min.js",
        "@syncfusion/ej2-documenteditor": "syncfusion:ej2-documenteditor/dist/ej2-documenteditor.umd.min.js"
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});

System.import('app');
```

## Adding CSS reference

Combined CSS files are available in the Essential JS 2 package root folder.
This can be referenced in your `[src/styles/styles.css]` using the following code.

```css
@import '../../node_modules/@syncfusion/ej2/material.css';
```

> To know about individual component CSS, please refer to
[Individual Component theme files](../appearance/theme#referring-individual-control-theme/) section.

## Adding component

You can add `DocumentEditorContainer` Component with  predefined toolbar and properties pane options or `DocumentEditor` component with customize options.

## DocumentEditor Component

DocumentEditor Component is used to create , view and edit word documents. In this , you can customize the UI options based on your requirements to modify the document.

### Adding DocumentEditor Component

You can start adding Essential JS 2 documenteditor component to the application. To get started, add the DocumentEditor component in `app.ts` and `index.html` files using the following code.

Place the following code in the `app.ts`.

```typescript
import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.enableAllModules();
documenteditor.appendTo('#DocumentEditor');

```

Now, add an HTML div element to act as the DocumentEditor element in `index.html` using the following code.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="shortcut icon" href="resources/favicon.ico" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <!--Element which will render as DocumentEditor -->
    <div id="DocumentEditor"></div>
</body>

</html>
```

### Run the DocumentEditor application

The quickstart project is configured to compile and run the application in the browser. Use the following command to run the application.

```sh
npm start
```

Documenteditor output will be displayed as follows.

{% tab template="document-editor/getting-started", isDefaultActive=true,es5Template="started" , sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Editor,Selection,OptionsPane, Search, ContextMenu, EditorHistory,ImageResizer, ListDialog,TableDialog, HyperlinkDialog, ParagraphDialog, FontDialog, PageSetupDialog, BookmarkDialog, StyleDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, TableOfContentsDialog } from '@syncfusion/ej2-documenteditor';

DocumentEditor.Inject(Editor,Selection,OptionsPane, Search, ContextMenu, EditorHistory,ImageResizer, ListDialog,TableDialog, HyperlinkDialog, ParagraphDialog, FontDialog, PageSetupDialog, BookmarkDialog, StyleDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, TableOfContentsDialog);

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.enableAllModules();
documenteditor.appendTo('#DocumentEditor');


```

{% endtab %}

## DocumentEditorContainer component

DocumentEditorContainer is a predefined component which wraps DocumentEditor, Toolbar, Properties pane, and Status bar into a single component. And the toolbar and properties pane is used to view and modify the document in DocumentEditor thought public APIs available in it.

### Adding DocumentEditorContainer component

You can start adding Essential JS 2 documenteditor container component to the application. To get started, add the DocumentEditorContainer component in `app.ts` and `index.html` files using the following code.

Place the following code in the `app.ts`.

```typescript
import { DocumentEditorContainer,Toolbar } from '@syncfusion/ej2-documenteditor';

DocumentEditorContainer.Inject(Toolbar);
let documenteditor: DocumentEditorContainer = new DocumentEditorContainer({
    enableToolbar: true
});
documenteditor.appendTo('#DocumentEditor');

```

Now, add an HTML div element to act as the DocumentEditorContainer element in `index.html` using the following code.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="shortcut icon" href="resources/favicon.ico" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <!--Element which will render as DocumentEditorContainer -->
    <div id="DocumentEditor"></div>
</body>

</html>
```

### Run the DocumentEditorContainer application

The quickstart project is configured to compile and run the application in the browser. Use the following command to run the application.

```sh
npm start
```

DocumentEditorContainer output will be displayed as follows.

{% tab template="document-editor/getting-started", isDefaultActive=true,es5Template="documenteditor" , sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditorContainer,Toolbar } from '@syncfusion/ej2-documenteditor';

DocumentEditorContainer.Inject(Toolbar);
let documenteditor: DocumentEditorContainer = new DocumentEditorContainer({
    enableToolbar: true
});
documenteditor.appendTo('#DocumentEditor');


```

{% endtab %}