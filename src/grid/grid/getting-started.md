---
title: "Getting Started"
component: "Grid"
description: "Learn how to create an Essential JS 2 DataGrid control and enable features like paging, filtering, sorting, and grouping."
---

# Getting Started

This section explains the steps to create a simple Grid and demonstrates the basic usage of the grid component using the Essential JS 2
[quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.
This seed repository is pre-configured with the Essential JS 2 package.

## Dependencies

Following is the list of minimum dependencies required to use the grid.

```javascript
|-- @syncfusion/ej2-grids
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-excel-export
        |-- @syncfusion/ej2-file-utils
        |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-pdf-export
        |-- @syncfusion/ej2-file-utils
        |-- @syncfusion/ej2-compression
```

## Setup for local development

Clone the Essential JS 2 quickstart application project from
[GitHub](https://github.com/syncfusion/ej2-quickstart.git), and
install the necessary npm packages using the following command line scripts.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

## Configuring system JS

**Syncfusion Grid packages** have to be mapped in the **system.config.js** configuration file.

```javascript
System.config({
    paths: {
         'npm:': './node_modules/',
         'syncfusion:': 'npm:@syncfusion/'
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-navigations": "syncfusion:ej2-navigations/dist/ej2-navigations.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-dropdowns": "syncfusion:ej2-dropdowns/dist/ej2-dropdowns.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-grids": "syncfusion:ej2-grids/dist/ej2-grids.umd.min.js",
        "@syncfusion/ej2-excel-export": "syncfusion:ej2-excel-export/dist/ej2-excel-export.umd.min.js",
        "@syncfusion/ej2-pdf-export": "syncfusion:ej2-pdf-export/dist/ej2-pdf-export.umd.min.js",
        "@syncfusion/ej2-file-utils": "syncfusion:ej2-file-utils/dist/ej2-file-utils.umd.min.js",
         "@syncfusion/ej2-querybuilder": "syncfusion:ej2-querybuilder/dist/ej2-querybuilder.umd.min.js",
        "@syncfusion/ej2-compression": "syncfusion:ej2-compression/dist/ej2-compression.umd.min.js"
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
[Individual Component theme files](../appearance/theme/#referring-individual-control-theme) section.

## Adding Grid component

You can start adding Essential JS 2 grid component to the application. To get started, add the grid component in **app.ts** and **index.html** files using the following code.

Place the following grid code in the **app.ts**.

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    height: 315
});

grid.appendTo('#Grid');

```

Now, add an HTML div element to act as the grid element in **index.html** using the following code.

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
    <!--Element which will render as Grid-->
    <div id="Grid"></div>
</body>

</html>
```

## Module injection

To create grids with additional features, inject the required modules. The following modules are used to extend grid's basic functionality.

* [`Page`](../api/grid/page/) - Inject this module to use paging feature.
* [`Sort`](../api/grid/sort/) - Inject this module to use sorting feature.
* [`Filter`](../api/grid/filter/) - Inject this module to use filtering feature.
* [`Group`](../api/grid/group/) - Inject this module to use grouping feature.
* **ExcelExport** - Inject this module to use Excel export feature.
* **PdfExport** - Inject this module to use PDF export feature.

These modules should be injected into the grid using the **Grid.Inject** method.

> Additional feature modules are available [`here`](../grid/module/).

## Enable paging

The paging feature enables users to view the grid record in a paged view. It can be enabled by setting the  [`allowPaging`](../api/grid/#allowpaging) property to true. Inject the [`Page`](../api/grid/page/)
 module as follows. If the [`Page`](../api/grid/page/) module is not injected, the pager will not be rendered in the grid. Pager can be customized using the [`pageSettings`](../api/grid/pageSettings/) property.

{% tab template="grid/grid",es5Template="enablepaging" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource';
Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    allowPaging: true,
    pageSettings: { pageSize: 7 }
});

grid.appendTo('#Grid');

```

{% endtab %}

## Enable sorting

The sorting feature enables you to order the records. It can be enabled by setting the  [`allowSorting`](../api/grid/#allowsorting) property as true. Inject the [`Sort`](../api/grid/sort/)
  module as follows. If [`Sort`](../api/grid/sort/) module is not injected, you cannot sort when a header is clicked. Sorting feature can be customized using the  [`sortSettings`](../api/grid/sortSettings/) property.

{% tab template="grid/grid",es5Template="enablesort" %}

```typescript
import { Grid, Sort, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource';

Grid.Inject(Sort, Page);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    allowSorting: true,
    allowPaging: true,
    pageSettings: { pageSize: 7 }
});

grid.appendTo('#Grid');


```

{% endtab %}

## Enable filtering

The filtering feature enables you to view reduced amount of records based on filter criteria. It can be enabled by setting the [`allowFiltering`](../api/grid/#allowfiltering) property as true.  The [`Filter`](../api/grid/filter/) module has to be injected as follows.
 If [`Filter`](../api/grid/filter/) module is not injected,  filter bar will not be rendered in the grid. Filtering feature can be customized using the [`filterSettings`](../api/grid/filterSettings/) property.

{% tab template="grid/grid",es5Template="enablefilter" %}

```typescript
import { Grid, Filter, Page, Sort } from '@syncfusion/ej2-grids';
import { data } from './datasource';

Grid.Inject(Filter, Page, Sort);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
               { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    allowFiltering: true,
    allowPaging: true,
    pageSettings: { pageSize: 6 },
    allowSorting: true
});

grid.appendTo('#Grid');


```

{% endtab %}

## Enable grouping

The grouping feature enables users to view the grid record in a grouped view. It can be enabled by setting the
 [`allowGrouping`](../api/grid/#allowgrouping) property to true.
 The [`Group`](../api/grid/group/) module has to be injected as follows. If [`Group`](../api/grid/group/) module is not injected, the group drop area will not be rendered in the grid.
 Grouping feature can be customized using the [`groupSettings`](../api/grid/groupSettings/) property.

{% tab template="grid/grid",es5Template="enablegroup" %}

```typescript
import { Grid, Group, Filter, Page, Sort } from '@syncfusion/ej2-grids';
import { data } from './datasource';

Grid.Inject(Group, Filter, Page, Sort);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    height: 175,
    allowGrouping: true,
    allowPaging: true,
    allowSorting: true,
    allowFiltering: true
});

grid.appendTo('#Grid');


```

{% endtab %}

## Run the application

The quickstart project is configured to compile and run the application in the browser. Use the following command to run the application.

```sh
npm start
```

Output will be displayed as follows.

{% tab template="grid/grid", isDefaultActive=true,es5Template="started" %}

```typescript
import { Grid, Group, Filter, Page, Sort } from '@syncfusion/ej2-grids';
import { data } from './datasource';

Grid.Inject(Group, Filter, Page, Sort);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    height: 175,
    allowGrouping: true,
    allowPaging: true,
    allowSorting: true,
    allowFiltering: true
});

grid.appendTo('#Grid');


```

{% endtab %}
