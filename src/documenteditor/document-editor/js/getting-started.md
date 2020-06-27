---
title: "Getting Started  with JavaScript(ES5)"
component: "DocumentEditor"
description: "Learn how to get started using JavaScript(global script) document editor component through simple steps."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2/) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-documenteditor/dist/global/ej2-documenteditor.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-documenteditor/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>
          <!-- EJ2 Document Editor dependent material theme -->
          <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/buttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/inputs/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/lists/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/navigations/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/splitbuttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <!-- EJ2 DocumentEditor material theme -->
          <link href="resources/documenteditor/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor dependent scripts -->
          <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-svg-base.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-file-utils.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-compression.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-pdf-export.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-splitbuttons.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-calendars.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-office-chart.min.js" type="text/javascript"></script>
          <!-- EJ2 Document Editor script -->
          <script src="resources/scripts/ej2-documenteditor.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Div` element and initiate the `Essential JS 2 DocumentEditor` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>
          <!-- EJ2 Document Editor dependent material theme -->
          <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/buttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/inputs/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/lists/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/navigations/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/splitbuttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <!-- EJ2 DocumentEditor material theme -->
          <link href="resources/documenteditor/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor dependent scripts -->
          <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-svg-base.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-file-utils.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-compression.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-pdf-export.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-splitbuttons.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-calendars.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-office-chart.min.js" type="text/javascript"></script>
          <!-- EJ2 Document Editor script -->
          <script src="resources/scripts/ej2-documenteditor.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--element which is going to render-->
                <div id='DocumentEditor'></div>
            <script>
                // Initialize DocumentEditor component.
                var documenteditor = new ej.documenteditor.DocumentEditor({ isReadOnly: false });

                documenteditor.acceptTab = true;
                documenteditor.enableAllModules();
                documenteditor.pageOutline = '#E0E0E0';

                //Documenteditor control rendering starts
                documenteditor.appendTo('#DocumentEditor');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 DocumentEditor** component.

**Step 7:** To render DocumentEditorContainer component, add the `Div` element and initiate the `Essential JS 2 DocumentEditorContainer` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>
          <!-- EJ2 Document Editor dependent material theme -->
          <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/buttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/inputs/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/lists/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/navigations/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/splitbuttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <!-- EJ2 DocumentEditor material theme -->
          <link href="resources/documenteditor/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor dependent scripts -->
          <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-svg-base.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-file-utils.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-compression.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-pdf-export.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-splitbuttons.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-calendars.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
          <script src="resources/scripts/ej2-office-chart.min.js" type="text/javascript"></script>
          <!-- EJ2 Document Editor script -->
          <script src="resources/scripts/ej2-documenteditor.min.js" type="text/javascript"></script>
       </head>
<body>
<!--element which is going to render-->
<div id='DocumentEditor' style='height:620px'>

</div>
<script>
    // Initialize DocumentEditorContainer component.
    var documenteditorContainer = new ej.documenteditor.DocumentEditorContainer({ enableToolbar: true });
    ej.documenteditor.DocumentEditorContainer.Inject(ej.documenteditor.Toolbar);
    documenteditorContainer.serviceUrl = 'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/import';
    //DocumentEditorContainer control rendering starts
    documenteditorContainer.appendTo('#DocumentEditor');
</script>
</body>
  </html>
```

Now, run the `index.html` in web browser, it will render the **Essential JS 2 DocumentEditorContainer** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `https://cdn.syncfusion.com/ej2/{RELEASE_VERSION}/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{RELEASE_VERSION}/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/dist/global/ej2-documenteditor.min.js`](https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/dist/global/ej2-documenteditor.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/styles/material.css`](https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Div` element and initiate the `Essential JS 2 DocumentEditor` component in the index.html by using following code.

{% tab template="document-editor/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>

          <!-- EJ2 Document Editor dependent theme -->
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-base/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-lists/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor theme -->
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor dependent scripts -->
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-svg-base/dist/global/ej2-svg-base.min.js"type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-file-utils/dist/global/ej2-file-utils.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-compression/dist/global/ej2-compression.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-pdf-export/dist/global/ej2-pdf-export.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-office-chart/dist/global/ej2-office-chart.min.js" type="text/javascript"></script>
          <!-- EJ2 Document Editor script -->
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/dist/global/ej2-documenteditor.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--element which is going to render-->
                <div id='DocumentEditor' style='height:350px'></div>
            <script>
                // Initialize DocumentEditor component.
                var documenteditor = new ej.documenteditor.DocumentEditor({ isReadOnly: false });

                documenteditor.acceptTab = true;
                documenteditor.enableAllModules();
                documenteditor.pageOutline = '#E0E0E0';

                //Documenteditor control rendering starts
                documenteditor.appendTo('#DocumentEditor');
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 DocumentEditor` component.

**Step 5:** To render DocumentEditorContainer component, add the `Div` element and initiate the `Essential JS 2 DocumentEditorContainer` component in the index.html by using following code.

{% tab template="document-editor/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>

          <!-- EJ2 Document Editor dependent theme -->
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-base/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-lists/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />
          <link href="https://cdn.syncfusion.com/ej2/17.3.14/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor theme -->
          <link href="http://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/styles/material.css" rel="stylesheet" type="text/css" rel='nofollow' />

          <!-- EJ2 Document Editor dependent scripts -->
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-svg-base/dist/global/ej2-svg-base.min.js"type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-file-utils/dist/global/ej2-file-utils.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-compression/dist/global/ej2-compression.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-pdf-export/dist/global/ej2-pdf-export.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-office-chart/dist/global/ej2-office-chart.min.js" type="text/javascript"></script>
          <!-- EJ2 Document Editor script -->
          <script src="https://cdn.syncfusion.com/ej2/17.3.14/ej2-documenteditor/dist/global/ej2-documenteditor.min.js" type="text/javascript"></script>
       </head>

<body>
<!--element which is going to render-->
<div id='DocumentEditor' style='height:620px'>

</div>
<script>
    // Initialize DocumentEditorContainer component.
    var documenteditorContainer = new ej.documenteditor.DocumentEditorContainer({ enableToolbar: true });
    ej.documenteditor.DocumentEditorContainer.Inject(ej.documenteditor.Toolbar);
    documenteditorContainer.serviceUrl = 'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/';
    //DocumentEditorContainer control rendering starts
    documenteditorContainer.appendTo('#DocumentEditor');
</script>
</body>

</html>
```

{% endtab %}

Now, run the `index.html` in web browser, it will render the `Essential JS 2 DocumentEditorContainer` component.