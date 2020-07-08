---
title: "Getting started"
component: "Pager"
description: "Learn how to add and customize the pager in the Essential JS 2."
---

# Getting started

This section explains you the steps required to create a simple Essential JS 2 Pager and demonstrate the basic usage of the Pager control in a JavaScript application.

## Dependencies

Below is the list of minimum dependencies required to use the Pager.

```javascript
|-- @syncfusion/ej2-base
|-- @syncfusion/ej2-grids
```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts and styles files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 Pager control.

## Adding Syncfusion resources

The Essential JS 2 Pager control can be initialized by using either of the following ways.

* Using local script and style.
* Using CDN link for script and style.

### Using local script and style

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the pager and its dependencies scripts and style file into the `resources/scripts` and `resources/styles` folder.

Refer the below code to find location pager's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-grids/dist/global/ej2-grids.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-grids/styles/material.css`

After copying the files, then you can refer the pager's scripts and styles into the `index.html` file.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Pager</title>
            <!-- Essential JS 2 material base style -->
            <link href="resources/styles/base/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 material theme -->
            <link href="resources/styles/grid/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Pager's dependent global script -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Pager's global script -->
            <script src="resources/scripts/ej2-grids.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script and style

Using CDN link, you can directly refer the pager control's script and style into the `index.html`.

Refer the pager's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js`](http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css)

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Pager</title>
            <!-- Essential JS 2 base material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 pager material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Pager's dependent global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Pager's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

## Adding Pager control

Now, you can start adding Pager control in the application. For getting started, add a `div` element for Pager control in `index.html`. Then refer the `index.js` file into the `index.html` file.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Pager</title>
            <!-- Essential JS 2 base material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 pager material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Pager's dependent global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Pager's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for pager  -->
             <div id="Pager"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following pager code in the `index.js`.

```javascript

var pager = ej.grids.Pager();
pager.appendTo('#Pager');

```

## Page Size

`pageSize` value defines the number records to be displayed per page. The default value for the `pageSize` is 12.

{% tab template="pager/pager", es5Template="pagesize" %}

```typescript
import {  Pager } from '@syncfusion/ej2-grids';

let pager: Pager = new Pager({
    totalRecordsCount: 20,
    pageSize: 1
});

pager.appendTo('#Pager');

```

{% endtab %}

## Page Count

`pageCount` value defines the number of pages to be displayed in the pager component for navigation.
The default value for `pageCount` is 10 and value will be updated based on `totalRecordsCount` and [`pageSize`](#pagesize) values.

{% tab template="pager/pager", es5Template="pagecount" %}

```typescript
import {  Pager } from '@syncfusion/ej2-grids';

let pager: Pager = new Pager({
    totalRecordsCount: 20,
    pageSize: 1,
    pageCount: 3
});

pager.appendTo('#Pager');

```

{% endtab %}

## Run the application

Now, run the `index.html` in web browser, it will render the Essential JS 2 Pager control.

Output will be appears as follows.

{% tab template="pager/pager" , isDefaultActive=true, es5Template="basic" %}

```typescript
import {  Pager } from '@syncfusion/ej2-grids';

let pager: Pager = new Pager({
    pageSize: 8,
    pageCount: 3,
    totalRecordsCount: 20,
});

pager.appendTo('#Pager');

```

{% endtab %}
