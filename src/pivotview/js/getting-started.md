---
title: "Getting Started ES-5"
component: "Pivot Table"
description: "Getting started section briefly explains on how to create and add a pivot table in an application."
---

# Getting Started

This section explains the steps to create a simple Essential JS 2 **Pivot Table** and demonstrates the basic usage of the pivot table control in a JavaScript application.

## Dependencies

The following list of dependencies are required to use the pivot table component in your application.

```javascript
|-- @syncfusion/ej2-pivotview
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-excel-export
        |-- @syncfusion/ej2-file-utils
        |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-pdf-export
        |-- @syncfusion/ej2-file-utils
        |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-charts
        |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-grids  
```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts and styles files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 pivot table control.

## Adding Syncfusion resources

The Essential JS 2 pivot table control can be initialized by using either of the following ways.

* Using local script and style.
* Using CDN link for script and style.

### Using local script and style

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the pivot table scripts and style file into the `resources/scripts` and `resources/styles` folder.

Refer the below code to find location pivot table's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-pivotview/dist/global/ej2-pivotview.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-pivotview/styles/material.css`

After copying the files, then you can refer the pivot table and its [dependency](#dependencies) scripts and styles into the **index.html** file.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 pivot table's dependent material theme -->
            <link href="resources/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 pivot table's material theme -->
            <link href="resources/ej2-pivotview/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 pivot table's dependent scripts -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-file-utils.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-compression.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-excel-export.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-pdf-export.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-calendars.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-grids.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 pivot table's global script -->
            <script src="resources/scripts/ej2-pivotview.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

> In this illustration, we have referred **material** theme. You can also refer other themes like bootstrap, fabric, high-contrast etc.,

### Using CDN link for script and style

Using CDN link, you can directly refer the pivot table control's script and style into the `index.html`.

Refer the pivot table's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-pivotview/dist/global/ej2-pivotview.min.js`](http://cdn.syncfusion.com/ej2/ej2-pivotview/dist/global/ej2-pivotview.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-pivotview/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-pivotview/styles/material.css)

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 pivot table's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 pivot table's material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-pivotview/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Grid's dependent scripts -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-file-utils/dist/global/ej2-file-utils.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-compression/dist/global/ej2-compression.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-excel-export/dist/global/ej2-excel-export.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-pdf-export/dist/global/ej2-pdf-export.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-svg-base/dist/global/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 pivot table's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-pivotview/dist/global/ej2-pivotview.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

<!-- markdownlint-disable MD028 -->

> In this illustration, we have referred **material** theme. You can also refer other themes like bootstrap, fabric, high-contrast etc.,

## Browser compatibility

Polyfills are required to use the Pivot Table in Internet Explorer 11 browser. Refer the [documentation](https://ej2.syncfusion.com/javascript/documentation/browser/?no-cache=1#browser-support) for more details.

## Initializing pivot table component in the application

Pivot Table component can be initialized using the following code. To get started, add the pivot table component in **index.js** and **index.html** files using the following code.

To get started, add **div** element for pivot table control in **index.html**. Then refer the **index.js** file into the **index.html** file.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 pivot table's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 pivot table's material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-pivotview/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Pivot table's dependent scripts -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-file-utils/dist/global/ej2-file-utils.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-compression/dist/global/ej2-compression.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-excel-export/dist/global/ej2-excel-export.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-pdf-export/dist/global/ej2-pdf-export.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-svg-base/dist/global/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 pivot table's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-pivotview/dist/global/ej2-pivotview.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for pivot table  -->
             <div id="PivotTable"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Next we need to initialize pivot table component using **ej.pivotview.PivotView()** instance as follows.

```javascript

var pivotTableObj = new ej.pivotview.PivotView();

```

## Assigning sample data to pivot table component

The sample data is assigned to the pivot table component through dataSource property under dataSourceSettings.

Place the following pivot table code in the `index.js`.

```javascript

var pivotData = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];
var pivotTableObj = new ej.pivotview.PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
    }
});
pivotTableObj.appendTo('#PivotTable');

```

## Adding fields to row, column, values and filters axes

Pivot Table component initialized and sample data assigned. Now add the fields to row, column, values and filters axes using following code.

* `rows`: Collection of fields that needs to be displayed in row axis of pivot table.
* `columns`: Collection of fields that needs to be displayed in column axis of pivot table.
* `values`: Collection of fields that needs to be displayed as aggregrated numeric values in pivot table.
* `filters`: Filter the values in other axis based on the collection of filter fields in pivot table.

In-order to define each field in the respective axis, the following basic properties should be set.

* `name`: It allows to set the field name from the bound data source. It’s casing should match exactly like in the data source and if not set properly, the pivot table will not be rendered.
* `caption`: It allows to set the field caption, which is the alias name of the field that needs to be displayed in the pivot table.
* `type`: It allows to set the summary type of the field. By default, SummaryType Sum is applied.

Place the following pivot table code in the `index.js`.

```javascript

var pivotData = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];
var pivotTableObj = new ej.pivotview.PivotView({
    dataSourceSettings: {
            dataSource: pivotData,
            expandAll: false,
            columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
            values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
            rows: [{ name: 'Country' }, { name: 'Products' }]
    }
});
pivotTableObj.appendTo('#PivotTable');

```

## Apply formatting to value fields

Formatting defines a way in which values should be displayed. For example, format “C” denotes the values should be displayed in currency pattern. To do so, define the name and format properties to formatSettings tag. In this illustration, the name property is set as Amount, a field from value section and its format is set as currency. Likewise, we can set format for other value fields as well and add it to formatSettings tag.

> Only fields from value axis, which is in the form of numeric data values are applicable for formatting.

Place the following pivot table code in the `index.js`.

```javascript

var pivotData = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];
var pivotTableObj = new ej.pivotview.PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
    }
});
pivotTableObj.appendTo('#PivotTable');

```

## Enable Grouping Bar

The Grouping Bar feature automatically populates fields from the bound data source and allows end users to drag fields between different axes such as columns, rows, values, and filters, and create pivot table at runtime. It can be enabled by setting the [`showGroupingBar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotViewModel/#showgroupingbar) property to **true**. To know more about grouping bar, [`refer`](./grouping-bar) here.

{% tab template="pivot-table/pivot-table", es5Template="groupingbar"%}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Enable Pivot Field List

The component provides a built-in Field List similar to Microsoft Excel. It allows you to add or remove fields and also rearrange the fields between different axes, including column, row, value, and filter along with filter and sort options dynamically at runtime. It can be enabled by setting the [`showFieldList`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotViewModel/#showfieldlist) property to **true**.

{% tab template="pivot-table/pivot-table", es5Template="fieldlist" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Calculated field

The calculated field feature allows user to insert or add a new calculated field based on the available fields from the bound data source. It can be customized using the [`calculatedFieldsSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/calculatedFieldSettings/) property through code behind. The setting required for calculate field feature at code behind are:
* [`name`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/calculatedFieldSettings/#name): it allows to indicate the given calculated field with unique name.
* [`formula`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/calculatedFieldSettings/#formula): it allows to set the formula base on the given data source.

Also calculated fields can be added at run time through the built-in dialog. The dialog can be enabled by setting the [`allowCalculatedField`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotViewModel/#allowcalculatedfield) property to **true**.

> Calculated field is applicable only for value fields.

{% tab template="pivot-table/calculatedfield", es5Template="calculatedfield" %}

```typescript
import { PivotView, IDataSet, CalculatedField} from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(CalculatedField);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
        calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
    },
    allowCalculatedField: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let btn: Button = new Button({ isPrimary: true }, '#CalculatedField');

document.getElementById('CalculatedField').addEventListener('click', () => {
    pivotTableObj.calculatedFieldModule.createCalculatedFieldDialog();
});

```

{% endtab %}

## Exploring Filter axis

The filter axis contains collection of fields that would act as master filter over the data bound in row, column and value axes of the pivot table. The fields along with filter members could be set to filter axis either through report via code behind or by dragging and dropping fields from other axes to filter axis via grouping bar or field list at runtime.

Place the following pivot table code in the `index.js`.

{% tab template="pivot-table/pivot-table", es5Template="filter-axis" %}

```typescript
import { PivotView, IDataSet, FieldList, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Products' }],
        filters:[{ name: 'Country' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showFieldList: true,
    showGroupingBar:true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Run the application

Now,  run the `index.html` in web browser, it will render the `Essential JS 2 pivot table` control.

Output will be displayed as follows.

{% tab template="pivot-table/pivot-table", es5Template="started", isDefaultActive=true %}

```typescript
import { PivotView, IDataSet, CalculatedField, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(CalculatedField, FieldList);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
        calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
    },
    showFieldList: true,
    allowCalculatedField: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Deploy the Application

The Essential JS 2 pivot table control features are segregated into individual feature-wise modules. The [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build and `CDN` scripts contains code for all features used in pivot table and hence we suggest to not to use them in production. We strongly recommend you to generate script files to use in production using our **Custom Resource Generator**[`(CRG)`](https://crg.syncfusion.com/) for Essential JS 2. CRG will allow you to generate the bundled script for the currently enabled features in pivot table.
