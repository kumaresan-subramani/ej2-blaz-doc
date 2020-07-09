---
title: "Getting Started"
component: "Pivot Table"
description: "Getting started section briefly explains on how to create and add a pivot table in an application."
---

# Getting Started

This section explains the steps to create a simple **Pivot Table** and demonstrates the basic usage of the pivot table component using the Essential JS 2 [quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.
This seed repository is pre-configured with the Essential JS 2 package.

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
    |-- @syncfusion/ej2-grids
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-navigations
```

## Setup for local development

* Clone the Essential JS 2 quickstart application project from
[GitHub](https://github.com/syncfusion/ej2-quickstart.git) using the command prompt, and
install the necessary npm packages using the following command line scripts.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

## Configuring system JS

[Syncfusion PivotView packages](#dependencies) have to be mapped in the `system.config.js` configuration file.

```typescript
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/'
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-navigations": "syncfusion:ej2-navigations/dist/ej2-navigations.umd.min.js",
        "@syncfusion/ej2-grids": "syncfusion:ej2-grids/dist/ej2-grids.umd.min.js",
        "@syncfusion/ej2-dropdowns": "syncfusion:ej2-dropdowns/dist/ej2-dropdowns.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-excel-export": "syncfusion:ej2-excel-export/dist/ej2-excel-export.umd.min.js",
        "@syncfusion/ej2-pdf-export": "syncfusion:ej2-pdf-export/dist/ej2-pdf-export.umd.min.js",
        "@syncfusion/ej2-file-utils": "syncfusion:ej2-file-utils/dist/ej2-file-utils.umd.min.js",
        "@syncfusion/ej2-compression": "syncfusion:ej2-compression/dist/ej2-compression.umd.min.js",
        "@syncfusion/ej2-pivotview": "syncfusion:ej2-pivotview/dist/ej2-pivotview.umd.min.js"
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

## Browser compatibility

Polyfills are required to use the Pivot Table in Internet Explorer 11 browser. Refer the [documentation](https://ej2.syncfusion.com/documentation/browser/?no-cache=1#browser-support) for more details.

## Initializing pivot table component in the application

Pivot Table component can be initialized using the following code. To get started, add the pivot table component in `app.ts` and `index.html` files using the following code.

Place the following pivot table code in the `app.ts`.

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';


let pivotTableObj: PivotView = new PivotView();
pivotTableObj.appendTo('#PivotTable');

```

Now, add an HTML div element which act as the pivot table element in `index.html` using the following code.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>pivot table Typescript Component</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css " />
     <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />
    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>
<body>
    <!--Element where the pivot table will be rendered-->
    <div id="PivotTable"></div>
</body>
</html>
```

## Assigning sample data to pivot table component

The sample data is assigned to the pivot table component through dataSource property under dataSourceSettings.

Place the following pivot table code in the `app.ts`.

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';

let pivotData: IDataSet[] = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
    },
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

Place the following pivot table code in the `app.ts`.

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';

let pivotData: IDataSet[] = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }],
        values: [{ name: 'Sold', caption: 'Units Sold', type: 'Sum' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [{ name: 'Quarter' }]
    },
});
pivotTableObj.appendTo('#PivotTable');

```

Now, add an HTML div element which act as the pivot table element in `index.html` using the following code.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>pivot table Typescript Component</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css " />
     <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />
    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>
<body>
    <!--Element where the pivot table will be rendered-->
    <div id="pivotTable"></div>
</body>
</html>
```

## Apply formatting to value fields

Formatting defines a way in which values should be displayed. For example, format “C” denotes the values should be displayed in currency pattern. To do so, define the name and format properties to formatSettings tag. In this illustration, the name property is set as Amount, a field from value section and its format is set as currency. Likewise, we can set format for other value fields as well and add it to formatSettings tag.

> Only fields from value axis, which is in the form of numeric data values are applicable for formatting.

Place the following pivot table code in the `app.ts`.

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';

let pivotData: IDataSet[] = [
            { 'Sold': 31, 'Amount': 52824, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q1' },
            { 'Sold': 51, 'Amount': 86904, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q2' },
            { 'Sold': 90, 'Amount': 153360, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q3' },
            { 'Sold': 25, 'Amount': 42600, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2015', 'Quarter': 'Q4' },
            { 'Sold': 27, 'Amount': 46008, 'Country': 'France', 'Products': 'Mountain Bikes', 'Year': 'FY 2016', 'Quarter': 'Q1' }];

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData,
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }],
        values: [{ name: 'Sold', caption: 'Units Sold', type: 'Sum' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [{ name: 'Quarter' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
    },
});
pivotTableObj.appendTo('#PivotTable');

```

## Module injection

To create pivot table with additional features, inject the required modules. The modules that are available with basic functionality are as follows.

* `GroupingBar` - Inject this module to access grouping bar feature.
* `FieldList` - Inject this module to access pivot field list feature.
* `CalculatedField` - Inject this module to access calculated field feature.

These modules should be injected into the pivot table using the `Inject` method within the `app.ts` file as shown below. On doing so, only the injected views will be loaded and displayed along with pivot table.

`[src/app/app.ts]`

```typescript
PivotView.Inject(GroupingBar);
```

## Enable Grouping Bar

The Grouping Bar feature automatically populates fields from the bound data source and allows end users to drag fields between different axes such as columns, rows, values, and filters, and create pivot table at runtime. It can be enabled by setting the `showGroupingBar` property to **true** and by injecting the `GroupingBar` module as follows.

> If the `GroupingBar` module is not injected, the grouping bar will not be rendered with the pivot table component.

{% tab template="pivot-table/pivot-table", es5Template="groupingbar", sourceFiles="index.ts,index.html" %}

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

The component provides a built-in Field List similar to Microsoft Excel. It allows you to add or remove fields and also rearrange the fields between different axes, including column, row, value, and filter along with filter and sort options dynamically at runtime. It can be enabled by setting the `showFieldList` property to **true** and by injecting the `FieldList` module as follows.

> If the `FieldList` module is not injected, the Field List will not be rendered with the pivot table component.

{% tab template="pivot-table/pivot-table", es5Template="fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
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

The calculated field feature allows user to insert or add a new calculated field based on the available fields from the bound data source. It can be customized using the `calculatedFieldsSettings` property through code behind. The setting required for calculate field feature at code behind are:
* `name`: it allows to indicate the given calculated field with unique name.
* `formula`: it allows to set the formula base on the given data source.

Also calculated fields can be added at run time through the built-in dialog. The dialog can be enabled by setting the `allowCalculatedField` property to **true** and by injecting the `CalculatedField` module as follows.

> If the `CalculatedField` module is not injected, the calculated field dialog will not be rendered with the pivot table component. Moreover calculated field is applicable only for value fields.

{% tab template="pivot-table/calculatedfield", es5Template="calculatedfield", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, CalculatedField, FieldList} from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(CalculatedField, FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Amount', type: 'CalculatedField' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
        calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
    },
    showFieldList: true,
    allowCalculatedField: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let btn: Button = new Button({ isPrimary: true });
btn.appendTo('#CalculatedField');

document.getElementById('CalculatedField').addEventListener('click', () => {
    pivotTableObj.calculatedFieldModule.createCalculatedFieldDialog();
});

```

{% endtab %}

## Exploring Filter axis

The filter axis contains collection of fields that would act as master filter over the data bound in row, column and value axes of the pivot table. The fields along with filter members could be set to filter axis either through report via code behind or by dragging and dropping fields from other axes to filter axis via grouping bar or field list at runtime.

Place the following pivot table code in the `app.ts`.

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

The quickstart project is configured to compile and run the application in the browser. Use the following command to run the application.

```sh
npm start
```

Output will be displayed as follows.

{% tab template="pivot-table/pivot-table", es5Template="started", isDefaultActive=true, sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, CalculatedField, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(CalculatedField, FieldList);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
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
