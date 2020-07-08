---
title: "Columns"
component: "Grid"
description: "Documentation on column reordering, resizing, header templates (custom header content), and column templates (custom cell content) in the Essential JS 2 DataGrid control."
---

# Columns

The column definitions are used as the [`dataSource`](../api/grid/#datasource) schema in the Grid. This plays a vital role in rendering column values in the required format.
The grid operations such as sorting, filtering and grouping etc. are performed based on column definitions. The [`field`](../api/grid/column/#field) property of the [`columns`](../api/grid/column)
is necessary to map the data source values in Grid columns.

> 1. If the column [`field`](../api/grid/column/#field) is not specified in the dataSource, the column values will be empty.
> 2. If the [`field`](../api/grid/column/#field) name contains “dot” operator, it is considered as complex binding.

## Auto generation

The [`columns`](../api/grid/column) are automatically generated when
[`columns`](../api/grid/column) declaration is empty or undefined while initializing the grid. All the columns in the [`dataSource`](../api/grid/#datasource) are bound as grid columns.

{% tab template="grid/row-template" , es5Template="autogenerate" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';

let data: Object[] = [
    { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5 },
    { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6 },
    { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4 }];

let grid: Grid = new Grid ({
    dataSource: data
});
grid.appendTo('#Grid');

```

{% endtab %}

> When columns are auto-generated, the column [`type`](../api/grid/column/#type) will be determined from the first record of the [`dataSource`](../api/grid/#datasource).

### Set isPrimaryKey for auto generated columns when editing is enabled

Primary key can be defined in the declaration of column object of the grid. When we didn't declare the columns, the grid will generate the columns automatically. For these auto generated columns, you can set [`isPrimaryKey`](../api/grid/column/#isprimarykey) column property as true by any one of the following two ways,

If Primary key "column index" is known then refer the following code example

```typescript

import { Grid, Edit } from '@syncfusion/ej2-grids';

Grid.Inject(Edit);

let data: Object[] = [
    { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5 },
    { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6 },
    { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4 }];

let grid: Grid = new Grid ({
    dataSource: data,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true }
});
grid.appendTo('#Grid');

grid.dataBound = () => {
    var column: Column = grid.columns[0];
    column.isPrimaryKey = 'true';
}

```

If Primary key "column fieldname" is known then refer the following code example

```typescript

import { Grid, Edit } from '@syncfusion/ej2-grids';

Grid.Inject(Edit);

let data: Object[] = [
    { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5 },
    { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6 },
    { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4 }];

let grid: Grid = new Grid ({
    dataSource: data,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true }
});
grid.appendTo('#Grid');

grid.dataBound = () => {
    var column: Column = grid.getColumnByField('OrderID');
    column.isPrimaryKey = 'true';
}

```

### Set column options to auto generated columns

You can set column options such as [`format`](../api/grid/column/#format), [`width`](../api/grid/column/#width) to the auto generated columns by using [`dataBound`](../api/grid/#databound) event of the grid.

In the below example, [`width`](../api/grid/column/#width) is set for **OrderID** column, **date** type is set for **OrderDate** column and **numeric** type is set for **Freight** column.

{% tab template="grid/row-template" , es5Template="autogenerateformat" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';

let data: Object[] = [
            { OrderID: 10248, CustomerID: 'VINET', Freight: 32.3800, OrderDate: "1996-07-02T00:00:00.000Z" },
            { OrderID: 10249, CustomerID: 'TOMSP', Freight: 32.3800, OrderDate: "1996-07-19T00:00:00.000Z" },
            { OrderID: 10250, CustomerID: 'HANAR', Freight: 32.3800, OrderDate: "1996-07-22T00:00:00.000Z" }];

let grid: Grid = new Grid ({
    dataSource: data,
    dataBound: dataBound
});
grid.appendTo('#Grid');

function dataBound(args: any): void {
        for (var i = 0; i < this.columns.length; i++) {
            this.columns[0].width = 120;
            if(this.columns[i].field === "OrderDate"){
                this.columns[i].type="date";
            }
            if (this.columns[i].type === "date") {
                this.columns[i].format = { type: "date", format: "dd/MM/yyyy" };
            }
            this.columns[2].format = "P2";
        }
        this.refreshColumns();
    }

```

{% endtab %}

## Complex data binding

You can achieve complex data binding in the grid by using the dot(.) operator in the [`column.field`](../api/grid/column/#field).

{% tab template="grid/complex-binding", sourceFiles="index.ts,datasource.ts", es5Template="databind"  %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { complexData } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: complexData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 100 },
        { field: 'Name.FirstName', headerText: 'First Name', width: 120 },
        { field: 'Name.LastName', headerText: 'Last Name', width: 100 },
        { field: 'Title', headerText: 'Title', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

For OData and ODataV4 adaptors, you need to add [`expand`](../api/data/query/#expand) query to the [`query`](../api/grid/#query) property (of Grid), to eager load the complex data.

```typescript
import { DataManager, ODataAdaptor, Query } from '@syncfusion/ej2-data';

 let  data: DataManager = new DataManager({
       adaptor: new ODataAdaptor(),
       crossDomain: true,
       url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders'
     });
 let query: Query = new Query().expand('Employee');

 let grid: Grid = new Grid({
    dataSource: data,
    query: query,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'Employee.City', headerText: 'Employee City', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

## Foreign Key Column

Foreign key column can be enabled by using [`column.dataSource`](../api/grid/column/#datasource), [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) and [`column.foreignKeyValue`](../api/grid/column/#foreignkeyvalue) properties.

* [`column.dataSource`](../api/grid/column/#datasource) - Defines the foreign data.
* [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) - Defines the mapping column name to the foreign data.
* [`column.foreignKeyValue`](../api/grid/column/#foreignkeyvalue) - Defines the display field from the foreign data.

In the following example, **Employee Name** is a foreign column which shows **FirstName** column from foreign data.

{% tab template="grid/foreign-key", es5Template="foreign-key" %}

```typescript
import { Grid, ForeignKey } from '@syncfusion/ej2-grids';
import { data, employeeData } from './datasource.ts';

Grid.Inject(ForeignKey);

let grid: Grid = new Grid(
    {
        dataSource: data.slice(0,10),
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            {
                field: 'EmployeeID', headerText: 'Employee Name', width: 150, foreignKeyValue: 'FirstName', dataSource: employeeData
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right'},
            { field: 'ShipName', headerText: 'Ship Name', width: 180 }
        ],
        height: 315
    });
grid.appendTo('#Grid');

```

{% endtab %}

> * For remote data, the sorting and grouping is done based on [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) instead of [`column.foreignKeyValue`](../api/grid/column/#foreignkeyvalue).
> * If [`column.foreignKeyField`](../api/grid/column/#foreignkeyfield) is not defined, then the column uses [`column.field`](../api/grid/column/#field).

## Header Template

You can customize the header element by using the [`headerTemplate`](../api/grid/column/#headerTemplate) property. In this demo, the custom element is rendered for both EmployeeID and BirthDate column headers.

{% tab template="grid/headertemplate", sourceFiles="index.ts,index.html", es5Template="headertemplate" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
         { field: 'EmployeeID', headerText: 'Employee ID', width: 120, textAlign: 'Right', headerTemplate: '#employeetemplate' },
                { field: 'FirstName', headerText: 'First Name', width: 140 },
                {
                    field: 'BirthDate', headerText: 'Birth Date', width: 130, format: 'yMd',
                    textAlign: 'Right', headerTemplate: '#datetemplate'
                },
                { field: 'City', width: 120 },
                { field: 'Country', headerText: 'Country', width: 140, format: 'yMd', textAlign: 'Right' },
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Header text

By default, column header title is displayed from column [`field`](../api/grid/column/#field) value. To override the default header title, you have to define the [`headerText`](../api/grid/column/#headertext) value.

{% tab template="grid/grid", es5Template="headertext" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 315
});

grid.appendTo('#Grid');

```

{% endtab %}

> * If both the [`field`](../api/grid/column/#field) and [`headerText`](../api/grid/column/#headertext)
are not defined in the column, the column renders with “empty” header text.

## Format

To format cell values based on specific culture, use the [`columns.format`](../api/grid/column/#format) property. The grid uses [Internalization](../common/internationalization/) library to format [`number`](../common/internationalization/#number-formatting) and [`date`](../common/internationalization/#date-formatting)
values.

{% tab template="grid/grid", es5Template="format" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 315
});

grid.appendTo('#Grid');

```

{% endtab %}

> By default, the [`number`](../common/internationalization/#number-formatting) and [`date`](../common/internationalization/#date-formatting) values are formatted in **en-US** locale. You can localize the currency and date in different locale as explained [`here`](../common/internationalization/)

### Number formatting

The number or integer values can be formatted using the below format strings.

Format |Description |Remarks
-----|-----
N | Denotes numeric type. | The numeric format is followed by integer value as N2, N3. etc which denotes the number of precision to be allowed.
C | Denotes currency type. | The currency format is followed by integer value as C2, C3. etc which denotes the number of precision to be allowed.
P | Denotes percentage type | The percentage format expects the input value to be in the range of 0 to 1. For example the cell value **0.2** is formatted as **20%**. The percentage format is followed by integer value as P2, P3. etc which denotes the number of precision to be allowed.

Please refer to the link to know more about [`Number formatting`](../common/internationalization/#number-formatting).

### Date formatting

You can format date values either using built-in date format string or custom format string.

For built-in date format you can specify [`columns.format`](../api/grid/column/#format) property as string   (Example: **yMd**). Please refer to the link to know more about [`Date formatting`](../common/internationalization/#date-formatting).

You can also use custom format string to format the date values. Some of the custom formats and the formatted date values are given in the below table.

Format | Formatted value
-----|-----
{ type:'date', format:'dd/MM/yyyy' } | 04/07/1996
{ type:'date', format:'dd.MM.yyyy' } | 04.07.1996
{ type:'date', skeleton:'short' } | 7/4/96
{ type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' } | 04/07/1996 12:00 AM
{ type: 'dateTime', format: 'MM/dd/yyyy hh:mm:ss a' } | 07/04/1996 12:00:00 AM

{% tab template="grid/pagerdropdown",es5Template="dateformat" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'Freight', headerText: 'Freight', format:'C2', width: 120 },
        { field: 'OrderDate',format: {type:'date', format:'dd/MM/yyyy'}, headerText:'Order Date', width:150},
        { field: 'OrderDate', format:{ type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' }, headerText: 'Ship Date', width: 180 }
    ],
});
grid.appendTo('#Grid');

```

{% endtab %}

## Visibility

You can hide any particular column in Grid before rendering by defining [`visible`](../api/grid/column/#visible) property as false. In the below sample **ShipCity** column is defined as visible false.

{% tab template="grid/grid", es5Template="visibility" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right',  width: 120, format: 'C' },
        { field: 'ShipCity', headerText: 'Ship City', width: 120 ,visible: false},
        { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 315
});

grid.appendTo('#Grid');

```

{% endtab %}

## AutoFit specific columns

The [`autoFitColumns`](../api/grid/#autofitcolumns) method resizes the column to fit the widest cell's content without wrapping. You can autofit a specific column at initial rendering by invoking the [`autoFitColumns`](../api/grid/#autofitcolumns) method in [`dataBound`](../api/grid/#dataBound) event.

To use the [`autoFitColumns`](../api/grid/#autofitcolumns) method, inject the **Resize** module in the grid.

{% tab template="grid/autofit-columns", es5Template="autofit" %}

```typescript
import { Grid, Resize } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Resize);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 140 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 130 },
        { field: 'ShipName', headerText: 'Ship Name', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 120 },
        { field: 'ShipAddress', headerText: 'Ship Address', width: 150 }
    ],
    dataBound: () => grid.autoFitColumns(['ShipName', 'ShipAddress']),
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

> You can autofit all the columns by invoking the [`autoFitColumns`](../api/grid/#autofitcolumns) method without column names.

## Reorder

Reordering can be done by drag and drop of a particular column header from one index to another index within the grid. To enable reordering, set the [`allowReordering`](../api/grid/#allowreordering) to true.

To use reordering, inject the [`Reorder`](../api/grid/reorder) module in the grid.

{% tab template="grid/row-template" , es5Template="reorder" %}

```typescript
import { Grid, Reorder } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Reorder);

let grid: Grid = new Grid({
    dataSource: data,
    allowReordering: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

> You can disable reordering a particular column by setting the [`columns.allowReordering`](../api/grid/column/#allowreordering) to **false**.

### Reorder Single Column

Grid have option to reorder Columns either by Interaction or by using the [`reorderColumns`](../api/grid/reorder/#reordercolumns)method. In the below sample, **ShipCity** column is reordered to last column position by using the method.

{% tab template="grid/reorder-single-column" , es5Template="reorderSingleColumn" %}

```typescript
import { Grid, Reorder } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Reorder);

let grid: Grid = new Grid({
    dataSource: data,
    allowReordering: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipRegion', headerText: 'Ship Region', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let reorderSingleColsBtn: Button = new Button();
reorderSingleColsBtn.appendTo('#reorderSingleCol');

document.getElementById('reorderSingleCol').addEventListener('click', () => {
    grid.reorderColumns('ShipCity','ShipName');
});

```

{% endtab %}

### Reorder Multiple Columns

User can reorder a single column at a time by Interaction. Sometimes we need to have reorder multiple columns at the same time, It can be achieved through programmatically by using [`reorderColumns`](../api/grid/reorder/#reordercolumns) method.

In the below sample, **Ship City** and **Ship Region** column is reordered to last column position.

{% tab template="grid/reorder-column" , es5Template="reorderbyColumn" %}

```typescript
import { Grid, Reorder } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Reorder);

let grid: Grid = new Grid({
    dataSource: data,
    allowReordering: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipRegion', headerText: 'Ship Region', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let reorderMultipleColsBtn: Button = new Button();
reorderMultipleColsBtn.appendTo('#reorderMultipleCols');

document.getElementById('reorderMultipleCols').addEventListener('click', () => {
    grid.reorderColumns(['ShipCity','ShipRegion'],'ShipName');
});

```

{% endtab %}

### Reorder Events

During the reorder action, the grid component triggers the below three events.

1. The [`columnDragStart`](../api/grid/#columndragstart) event triggers when column header element drag (move) starts.
2. The [`columnDrag`](../api/grid/#columndrag) event triggers when column header element is dragged (moved) continuously.
3. The [`columnDrop`](../api/grid/#columndrop) event triggers when a column header element is dropped on the target column.

{% tab template="grid/row-template" , es5Template="reorderEvents" %}

```typescript
import { Grid, Reorder } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Reorder);

let grid: Grid = new Grid({
    dataSource: data,
    allowReordering: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    columnDragStart: () => {
        alert('columnDragStart event is Triggered');
    },
    columnDrag: () => {
        alert('columnDrag event is Triggered');
    },
    columnDrop: () => {
        alert('columnDrop event is Triggered');
    }
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Lock Columns

You can lock columns by using [`column.lockColumn`](../api/grid/column/#lockColumn) property. The locked columns will be moved to the first position. Also you can’t reorder its position.

In the below example, **Ship City** column is locked and its reordering functionality is disabled.

{% tab template="grid/lock-column", sourceFiles="index.ts,lock.css", es5Template="lockcolumn" %}

```typescript
import { Grid, Reorder } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Reorder);

let grid: Grid = new Grid({
    dataSource: data,
    allowReordering: true,
    allowSelection: false,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City',width: 100, lockColumn: true, customAttributes: {class: 'customcss'}},
        { field: 'ShipName', headerText: 'Ship Name', width: 100 },
        { field: 'ShipPostalCode', headerText: 'Ship Postal code', width: 100 },
        { field: 'ShipRegion', headerText: 'Ship Region', width: 100 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Column resizing

Column width can be resized by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. Each column can be auto resized by double-clicking the right edge of the column header to fit the width of that column based on the widest cell content. To enable column resize, set the [`allowResizing`](../api/grid/#allowresizing) property to true.

To use the column resize, inject **Resize** module in the grid.

{% tab template="grid/row-template", es5Template="resize" %}

```typescript
import { Grid, Resize } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Resize);

let grid: Grid = new Grid({
    dataSource: data,
    allowResizing: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width:150 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'Freight', headerText: 'Freight', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 },
        { field: 'ShipAddress', headerText: 'Ship Address', width: 150 },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 },
        { field: 'ShipPostalCode', headerText: 'Ship Postal code', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

> * You can disable resizing for a particular column by setting the [`columns.allowResizing`](../api/grid/column/#allowresizing) to false.
> * In RTL mode, you can click and drag the left edge of the header cell to resize the column.

### Column Resizing Externally

To resize a column, set width to that particular column and then refresh the grid header by using the [`refreshHeader()`](../api/grid/#refreshheader) method. Please refer the below code

```typescript

var grid = document.getElementById('Grid').ej2_instances[0]; //Grid Instance

var columns = grid.columns;

columns[0].width = 150;

grid.refreshHeader();

```

### Min and max width

Column resize can be restricted between minimum and maximum width by defining the [`columns->minWidth`](../api/grid/column/#minwidth) and [`columns->maxWidth`](../api/grid/column/#maxwidth).

In the following sample, minimum and maximum width are defined for **OrderID**, **Ship Name**, and **Ship Country** columns.

{% tab template="grid/row-template", es5Template="minmax" %}

```typescript
import { Grid, Resize } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Resize);

let grid: Grid = new Grid({
    dataSource: data,
    allowResizing: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', minWidth: 100, width: 150, maxWidth: 300 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'Freight', headerText: 'Freight', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name',  minWidth: 120, width: 150, maxWidth: 250  },
        { field: 'ShipAddress', headerText: 'Ship Address', width: 150 },
        { field: 'ShipCountry', headerText: 'Ship Country',  minWidth: 150, width: 200, maxWidth: 350  },
        { field: 'ShipPostalCode', headerText: 'Ship Postal code', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

### Resize Stacked Column

Stacked columns can be resized by clicking and dragging the right edge of the stacked column header. While dragging, the width of the respective child columns will be resized at the same time. You can disable resize for any particular stacked column by setting [`allowResizing`](../api/grid/#allowresizing) as **false** to its columns.

In this example, we have disabled resize for **Ship City** column.

{% tab template="grid/row-template", es5Template="stackedresize" %}

```typescript
import { Grid, Resize } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Resize);

let grid: Grid = new Grid({
    dataSource: data,
    allowResizing: true,
    columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, minWidth: 10 },
            {
                headerText: 'Order Details', columns: [
                    { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 125, minWidth: 10, format: 'yMd' },
                    { field: 'Freight', headerText: 'Freight($)', textAlign: 'Right', width: 100, format: 'C2', minWidth: 10 },
                ]
            },
            {
                headerText: 'Ship Details', columns: [
                    { field: 'ShipCity', headerText: 'Ship City', width: 100, minWidth: 10, allowResizing: false },
                    { field: 'ShipCountry', headerText: 'Ship Country', width: 120, minWidth: 10 },
                ]
            }
        ]
});
grid.appendTo('#Grid');

```

{% endtab %}

### Touch interaction

When the right edge of the header cell is tapped, a floating handler will be visible over the right border of the column. To resize the column, tap and drag the floating handler as needed. You can autoFit a column by using the Column menu of the grid.

The following screenshot represents the column resizing in touch device.

![Touch interaction image](images/column-resizing.jpg)

### Resizing Events

During the resizing action, the grid component triggers the below three events.

1. The [`resizeStart`](../api/grid/#resizestart) event triggers when column resize starts.
2. The [`resizing`](../api/grid/#resizing) event triggers when column header element is dragged (moved) continuously..
3. The [`resizeStop`](../api/grid/#resizestop) event triggers when column resize ends.

{% tab template="grid/row-template", es5Template="resizeevents" %}

```typescript
import { Grid, Resize } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Resize);

let grid: Grid = new Grid({
    dataSource: data,
    allowResizing: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width:150 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'Freight', headerText: 'Freight', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 },
        { field: 'ShipAddress', headerText: 'Ship Address', width: 150 },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 },
        { field: 'ShipPostalCode', headerText: 'Ship Postal code', width: 150 }
    ],
    height: 315,
    resizeStart: () => {
        alert('resizeStart event is Triggered');
    },
    resizing: () => {
        alert('Resizing event is Triggered');
    },
    resizeStop: () => {
        alert('resizeStop event is Triggered');
    }
});
grid.appendTo('#Grid');

```

{% endtab %}

## Column template

The column [`template`](../api/grid/column/#template) has options to display custom element instead of a field value in the column.

{% tab template="grid/column-template", sourceFiles="index.ts,index.html", es5Template="template" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        {
            headerText: 'Employee Image', textAlign: 'Center',
            template: '#template', width: 150
        },
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 125 },
        { field: 'FirstName', headerText: 'Name', width: 120 },
        { field: 'Title', headerText: 'Title', width: 170 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}
> Grid actions such as editing, grouping, filtering and sorting etc. will depend upon the column [`field`](../api/grid/column/#field). If the [`field`](../api/grid/column/#field) is not specified in the
template column, the grid actions cannot be performed.

### Using condition template

You can render the template elements based on condition.

In the following code, checkbox is rendered based on **Discontinued** field value.

```html
  <script id="template" type="text/x-template">
            <div class="template_checkbox">
                ${if(Discontinued)}
                <input type="checkbox" checked> ${else}
                <input type="checkbox"> ${/if}
            </div>
        </script>
```

{% tab template="grid/condition-inside-template", sourceFiles="index.ts,index.html", es5Template="condition-template" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { productData } from './datasource.ts';

let grid: Grid = new Grid({
        dataSource: productData,
        columns: [
            {
                headerText: 'Discontinued', textAlign: 'Center',
                template: '#template', width: 120
            },
            { field: 'ProductID', headerText: 'Product ID', textAlign: 'Right', width: 80 },
            { field: 'ProductName', headerText: 'Name', width: 160 },
            { field: 'SupplierID', headerText: 'SupplierID', width: 80 },
            { field: 'UnitsInStock', headerText: 'Stock', width: 80, textAlign: 'Right' }
        ],
        height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Column type

Column type can be specified using the [`columns.type`](../api/grid/column/#type) property. It specifies the type of data the column binds.

If the [`format`](../api/grid/column/#format)  is defined for a column, the column uses [`type`](../api/grid/column/#type) to select the appropriate format option ([number](../common/internationalization/#number-formatting)
 or [date](../common/internationalization/#manipulating-datetime)).

Grid column supports the following types:
* string
* number
* boolean
* date
* datetime

> If the [`type`](../api/grid/column/#type) is not defined, it will be determined from the first record of the [`dataSource`](../api/grid/#datasource).
> Incase if the first record of the [`dataSource`](../api/grid/#datasource) is null/blank value for a column then it is necessary to define the [`type`](../api/grid/column/#type) for that column.

## Column chooser

The column chooser has options to show or hide columns dynamically. It can be enabled by defining the
[`showColumnChooser`](../api/grid/#showcolumnchooser) as true.

To use the column chooser, inject the **ColumnChooser** module in the grid.

{% tab template="grid/columnchooser", es5Template="chooser" %}

```typescript
import { Grid, Selection, Toolbar, ColumnChooser } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Selection, Toolbar, ColumnChooser);

let grid: Grid = new Grid({
    dataSource: data,
    showColumnChooser: true,
    toolbar: ['ColumnChooser'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right' },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150, showInColumnChooser: false },
        { field: 'OrderDate', headerText: 'Order Date', width: 130, format: 'yMd', textAlign: 'Right' },
        { field: 'Freight', width: 120, format: 'C2', textAlign: 'Right' },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', visible: false, width: 150 }
    ],
    height: 235
});

grid.appendTo('#Grid');

```

{% endtab %}

> You can hide the column names in column chooser by defining the [`columns.showInColumnChooser`](../api/grid/column/#showincolumnchooser) as false.

### Open column chooser by external button

The Column chooser can be displayed on a page through external button by invoking
the [`openColumnChooser`](../api/grid/columnChooser) method with **X** and **Y** axis positions.

{% tab template="grid/columnchooser-method", sourceFiles="index.ts,index.html", es5Template="columnchooser"%}

```typescript
import { Grid, Selection, ColumnChooser } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Selection, ColumnChooser);

let grid: Grid = new Grid({
    dataSource: data,
    showColumnChooser: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right' },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150, showInColumnChooser: false },
        { field: 'OrderDate', headerText: 'Order Date', width: 130, format: 'yMd', textAlign: 'Right' },
        { field: 'Freight', width: 120, format: 'C2', textAlign: 'Right' },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', visible: false, width: 150 }

    ],
    height: 235
});

grid.appendTo('#Grid');

let show: Button = new Button({ cssClass: 'e-flat' }, '#show');

document.getElementById('show').onclick = () => {
    grid.columnChooserModule.openColumnChooser(200, 50); // give X and Y axis
};

```

{% endtab %}

## Column menu

The column menu has options to integrate features like sorting, grouping, filtering, column chooser, and autofit. It will show a menu with the integrated feature when users click on multiple icon of the column. To enable column menu, you need to define the [`showColumnMenu`](../api/grid/#showcolumnmenu) property as true.

To use the column menu, inject the **ColumnMenu** module in the grid.

The default items are displayed in following table.

| Item | Description |
|-----|-----|
| **SortAscending** | Sort the current column in ascending order. |
| **SortDescending** | Sort the current column in descending order. |
| **Group** | Group the current column. |
| **Ungroup** | Ungroup the current column. |
| **AutoFit** | Auto fit the current column. |
| **AutoFitAll** | Auto fit all columns. |
| **ColumnChooser** | Choose the column visibility. |
| **Filter** | Show the filter option as given in [`filterSettings.type`](../api/grid/filterSettings/#type) |

{% tab template="grid/row-template", es5Template="columnmenu" %}

```typescript
import { Grid, Resize, Sort, Group, Filter, ColumnMenu, Page } from '@syncfusion/ej2-grids';
import { data  } from './datasource.ts';

Grid.Inject(Resize, Sort, Group, Filter, ColumnMenu, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    allowSorting: true,
    allowFiltering: true,
    filterSettings: { type: 'CheckBox' },
    allowPaging: true,
    groupSettings: { showGroupedColumn: true },
    showColumnMenu: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 200, textAlign: 'Right',
            showInColumnChooser: false },
        { field: 'Freight', width: 150, format: 'C2', textAlign: 'Right', editType: 'numericedit' },
        { field: 'ShipName', headerText: 'Ship Name', width: 300 },
        { field: 'ShipCountry', headerText: 'Ship Country', visible: false, width: 200 },
        { field: 'ShipCity', headerText: 'Ship City', width: 200 }
    ]
});
grid.appendTo('#Grid');


```

{% endtab %}

> * You can disable column menu for a particular column by defining the [`columns.showColumnMenu`](../api/grid/column/#showcolumnmenu) as false.
> * You can customize the default items by defining the [`columnMenuItems`](../api/grid/#columnmenuitems) with required items.

### Column menu events

During the resizing action, the grid component triggers the below two events.

1. The [`columnMenuOpen`](../api/grid/#columnmenuopen) event triggers before the column menu opens.
2. The [`columnMenuClick`](../api/grid/#columnmenuclick) event triggers when the user clicks the column menu of the grid.

{% tab template="grid/row-template", es5Template="columnmenuevents" %}

```typescript
import { Grid, Resize, Sort, Group, Filter, ColumnMenu, Page } from '@syncfusion/ej2-grids';
import { data  } from './datasource.ts';

Grid.Inject(Resize, Sort, Group, Filter, ColumnMenu, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    allowSorting: true,
    allowFiltering: true,
    filterSettings: { type: 'CheckBox' },
    allowPaging: true,
    groupSettings: { showGroupedColumn: true },
    showColumnMenu: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 200, textAlign: 'Right',
            showInColumnChooser: false },
        { field: 'Freight', width: 150, format: 'C2', textAlign: 'Right', editType: 'numericedit' },
        { field: 'ShipName', headerText: 'Ship Name', width: 300 },
        { field: 'ShipCountry', headerText: 'Ship Country', visible: false, width: 200 },
        { field: 'ShipCity', headerText: 'Ship City', width: 200 }
    ],
    columnMenuOpen: () => {
        alert('columnMenuOpen event is Triggered');
    },
    columnMenuClick: () => {
        alert('columnMenuClick event is Triggered');
    }
});
grid.appendTo('#Grid');


```

{% endtab %}

### Custom Column Menu Item

Custom column menu items can be added by defining the [`columnMenuItems`](../api/grid/#columnmenuitems) as collection of
the [`columnMenuItemModel`](../api/grid/columnMenuItemModel).
Actions for this customized items can be defined in the [`columnMenuClick`](../api/grid/#columnmenuclick) event.

{% tab template="grid/row-template" , es5Template="custommenu" %}

```typescript
import { Grid, ColumnMenu, Sort, Page } from '@syncfusion/ej2-grids';
import { MenuEventArgs } from '@syncfusion/ej2-navigations';
import { data  } from './datasource.ts';

Grid.Inject(ColumnMenu, Page, Sort);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowSorting: true,
    showColumnMenu: true,
    columnMenuItems:[{text:'Clear Sorting', id:'gridclearsorting'}],
    columnMenuClick: function(args: MenuEventArgs){
        if(args.item.id === 'gridclearsorting'){
            grid.clearSorting();
        }
    },
    sortSettings:{
        columns:[{direction: "Ascending", field: "OrderID"}]
    },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 200, textAlign: 'Right', showInColumnChooser: false },
        { field: 'Freight', width: 150, format: 'C2', textAlign: 'Right', editType: 'numericedit' },
        { field: 'ShipName', headerText: 'Ship Name', width: 300 },
        { field: 'ShipCountry', headerText: 'Ship Country', visible: false, width: 200 },
        { field: 'ShipCity', headerText: 'Ship City', width: 200 }
    ]
});
grid.appendTo('#Grid');


```

{% endtab %}

### Customize menu items for particular columns

Sometimes, you have a scenario that to hide an item from column menu for particular columns. In that case, you need to define the [`columnMenuOpenEventArgs.hide`](../api/grid/columnMenuOpenEventArgs) as true in the [`columnMenuOpen`](../api/grid/#columnmenuopen) event.

The following sample, **Filter** item was hidden in column menu when opens for the **OrderID** column.

{% tab template="grid/row-template", es5Template="menuitems" %}

```typescript
import { Grid, ColumnMenu, Sort, Page, Resize, Group, Filter, ColumnMenuOpenEventArgs, ColumnMenuItemModel } from '@syncfusion/ej2-grids';
import { data  } from './datasource.ts';

Grid.Inject(ColumnMenu, Page, Group, Sort, Resize, Filter);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    showColumnMenu: true,
    filterSettings: {type: 'Menu'},
    allowFiltering: true,
    allowGrouping: true,
    allowSorting: true,
    columnMenuOpen: function (args: ColumnMenuOpenEventArgs) {
        for (let item of args.items) {
            if (item.text === 'Filter' && args.column.field === 'OrderID') {
                (item as ColumnMenuItemModel).hide = true;
            } else {
                (item as ColumnMenuItemModel).hide = false;
            }
        }
    },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 200, textAlign: 'Right', showInColumnChooser: false },
        { field: 'Freight', width: 150, format: 'C2', textAlign: 'Right', editType: 'numericedit' },
        { field: 'ShipName', headerText: 'Ship Name', width: 300 },
        { field: 'ShipCountry', headerText: 'Ship Country', visible: false, width: 200 },
        { field: 'ShipCity', headerText: 'Ship City', width: 200 }
    ]
});
grid.appendTo('#Grid');


```

{% endtab %}

## Column spanning

The grid has option to span the adjacent cells. You need to define the [`colSpan`](../api/grid/queryCellInfoEventArgs/#colspan) attribute to span cells in the [`QueryCellInfo`](../api/grid/queryCellInfoEventArgs) event.

In the following demo, employee **Davolio** is doing analysis from 9.00 A.M. to 10.00 A.M. so that the cells have been spanned.

{% tab template="grid/column-spanning", sourceFiles="index.ts,index.html", es5Template="span" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { columnSpanData, ColumnSpanDataType  } from './datasource.ts';

let grid: Grid = new Grid({
            dataSource: columnSpanData,
            queryCellInfo: QueryCellEvent,
            gridLines: 'Both',
            columns: [
                { field: 'EmployeeID', headerText: 'Employee ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
                { field: 'EmployeeName', headerText: 'Employee Name', width: 200 },
                { field: '9:00', headerText: '9.00 AM', width: 100 },
                { field: '9:30', headerText: '9.30 AM', width: 100 },
                { field: '10:00', headerText: '10.00 AM', width: 100 },
                { field: '10:30', headerText: '10.30 AM', width: 100 },
                { field: '11:00', headerText: '11.00 AM', width: 100 },
                { field: '11:30', headerText: '11.30 AM', width: 100 },
                { field: '12:00', headerText: '12.00 PM', width: 100 },
                { field: '12:30', headerText: '12.30 PM', width: 100 },
                { field: '2:30', headerText: '2.30 PM', width: 120 },
                { field: '3:00', headerText: '3.00 PM', width: 120 },
                { field: '3:30', headerText: '3.30 PM', width: 120 },
                { field: '4:00', headerText: '4.00 PM', width: 100 },
                { field: '4:30', headerText: '4.30 PM', width: 100 },
                { field: '5:00', headerText: '5.00 PM', width: 100 }
            ],
            width: 'auto',
            height: 'auto',
            allowTextWrap: true
});
grid.appendTo('#Grid');

function QueryCellEvent(args: QueryCellInfoEventArgs): void {
    let data: ColumnSpanDataType = args.data as ColumnSpanDataType;
    switch (data.EmployeeID) {
        case 10001:
            if (args.column.field === '9:00' || args.column.field === '2:30' || args.column.field === '4:30') {
                args.colSpan = 2;
            } else if (args.column.field === '11:00') {
                args.colSpan = 3;
            }
            break;
        case 10002:
            if (args.column.field === '9:30' || args.column.field === '2:30' ||
                args.column.field === '4:30') {
                args.colSpan = 3;
            } else if (args.column.field === '11:00') {
                args.colSpan = 4;
            }
            break;
        case 10003:
            if (args.column.field === '9:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '10:30' || args.column.field === '3:30' ||
                args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10004:
            if (args.column.field === '9:00') {
                args.colSpan = 3;
            } else if (args.column.field === '11:00') {
                args.colSpan = 4;
            } else if (args.column.field === '4:00' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10005:
            if (args.column.field === '9:00') {
                args.colSpan = 4;
            } else if (args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '3:30' || args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 10006:
            if (args.column.field === '9:00' || args.column.field === '4:30' ||
                args.column.field === '2:30' || args.column.field === '3:30') {
                args.colSpan = 2;
            } else if (args.column.field === '10:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            }
            break;
        case 10007:
            if (args.column.field === '9:00' || args.column.field === '3:00' || args.column.field === '10:30') {
                args.colSpan = 2;
            } else if (args.column.field === '11:30' || args.column.field === '4:00') {
                args.colSpan = 3;
            }
            break;
        case 10008:
            if (args.column.field === '9:00' || args.column.field === '10:30' || args.column.field === '2:30') {
                args.colSpan = 3;
            } else if (args.column.field === '4:00') {
                args.colSpan = 2;
            }
            break;
        case 10009:
            if (args.column.field === '9:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '4:30' || args.column.field === '2:30') {
                args.colSpan = 2;
            }
            break;
        case 100010:
            if (args.column.field === '9:00' || args.column.field === '2:30' ||
                args.column.field === '4:00' || args.column.field === '11:30') {
                args.colSpan = 3;
            } else if (args.column.field === '10:30') {
                args.colSpan = 2;
            }
            break;
    }
}

```

{% endtab %}

## Responsive columns

You can toggle column visibility based on media queries which are defined
at the [`hideAtMedia`](../api/grid/column/#hideatmedia).
The [`hideAtMedia`](../api/grid/column/#hideatmedia) accepts valid
[Media Queries]( http://cssmediaqueries.com/what-are-css-media-queries.html ). In the below sample, for **OrderID** column, [`hideAtMedia`](../api/grid/column/#hideatmedia) property value is set as **(min-width: 700px)** so that **OrderID** column will gets hidden when the browser screen width is lessthan 700px.

{% tab template="grid/hide-media", sourceFiles="index.ts,index.html", es5Template="responsive" %}

```typescript
import { Grid, Selection } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Selection);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        {
            field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right',
            hideAtMedia: '(min-width: 700px)'
        }, // column hides when browser screen width lessthan 700px;

        {
            field: 'CustomerID', headerText: 'Customer ID', width: 150,
            hideAtMedia: '(max-width: 500px)'
        }, // column shows when browser screen width lessthan or equalto 500px;

        {
            field: 'OrderDate', headerText: 'Order Date', width: 130, format: 'yMd',
            textAlign: 'Right', hideAtMedia: '(min-width:500px)'
        },// column hides when browser screensize lessthan 500px;

        { field: 'Freight', width: 120, format: 'C2', textAlign: 'Right' } // it always shown

    ],
    height: 315
});

grid.appendTo('#Grid');

```

{% endtab %}

## Controlling Grid actions

You can enable or disable grid action for a particular column by setting the [`allowFiltering`](../api/grid/#allowfiltering),
[`allowGrouping`](../api/grid/#allowgrouping), [`allowSorting`](../api/grid/#allowsorting), [`allowReordering`](../api/grid/#allowreordering), and [`allowEditing`](../api/grid/#editsettings) properties.

{% tab template="grid/grouping", es5Template="control" %}

```typescript
import { Grid, Group, Sort, Filter, Edit, Reorder } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group, Sort, Filter, Edit, Reorder);

let grid: Grid = new Grid({
    dataSource: data,
    allowFiltering: true,
    allowGrouping: true,
    allowSorting: true,
    allowReordering: true,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', allowGrouping: false, textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', allowFiltering: false, allowReordering: false, allowEditing: false, width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', allowSorting: false, width: 100 }
    ],
    height: 220
});
grid.appendTo('#Grid');


```

{% endtab %}

## Show/hide columns by external button

You can show or hide grid columns dynamically using external buttons by invoking the [`showColumns`](../api/grid/#showcolumns) or [`hideColumns`](../api/grid/#hidecolumns) method.

{% tab template="grid/show-hide-columns", sourceFiles="index.ts,index.html", es5Template="showhide"%}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let show: Button = new Button({ cssClass: 'e-flat' }, '#show');
let hide: Button = new Button({ cssClass: 'e-flat' }, '#hide');

document.getElementById('show').onclick = () => {
    grid.showColumns(['Customer ID', 'Ship Name']); //show by HeaderText
};

document.getElementById('hide').onclick = () => {
    grid.hideColumns(['Customer ID', 'Ship Name']); //hide by HeaderText
};

```

{% endtab %}

## ValueAccessor

The [`valueAccessor`](../api/grid/column/#valueaccessor) is used to access/manipulate the value of display data. You can achieve custom value formatting by using the [`valueAccessor`](../api/grid/column/#valueaccessor).

{% tab template="grid/value-accessor", sourceFiles="index.ts,index.html,datasource.ts", es5Template="value" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', width: 100, valueAccessor: currencyFormatter },
        { field: 'ShipName', headerText: 'Ship Name', width: 180, valueAccessor: valueAccess }
    ],
    height: 315
});
grid.appendTo('#Grid');

function currencyFormatter(field: string, data: Object, column: Object): string {
    return '€' + data['Freight'];
}

function valueAccess(field: string, data: Object, column: Object): string {
    return data[field] + '-' + data['ShipRegion'];
}

```

{% endtab %}

### Display array type columns

You can bind an array of objects in a column by using the [`valueAccessor`](../api/grid/column/#valueaccessor) property.
In this example, the name field has an array of two objects, FirstName and LastName. These two objects are joined and bound to a column using the
[`valueAccessor`](../api/grid/column/#valueaccessor).
{% tab template="grid/array-of-string", sourceFiles="index.ts,index.html,datasource.ts", es5Template="array"%}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { stringData } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: stringData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 100 },
        { field: 'Name', headerText: 'Full Name', width: 120, valueAccessor: valueAccess },
        { field: 'Title', headerText: 'Title', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

function valueAccess(field: string, data: Object, column: Object): string {
    return data[field].map(function (s: {LastName: string, FirstName: string}): string {
        return s.LastName || s.FirstName }).join(' ');
}

```

{% endtab %}

### Expression column

You can achieve the expression column by using the [`valueAccessor`](../api/grid/column/#valueaccessor) property.

{% tab template="grid/expression", es5Template="expression" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { foodInformation } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: foodInformation,
    columns: [
        { field: 'FoodName', headerText: 'FoodName', width: 120 },
        { field: 'Protein', headerText: 'Protein', textAlign: 'Right', width: 100 },
        { field: 'Fat', headerText: 'Fat', textAlign: 'Right', width: 100 },
        { field: 'Carbohydrate', headerText: 'Carbohydrate', textAlign: 'Right', width: 130 },
        { headerText: 'Calories In Take', valueAccessor: totalCalories, textAlign: 'Right', width: 150 },
    ],
    height: 315
});
grid.appendTo('#Grid');

function totalCalories(field: string, data: { Protein: number, Fat: number, Carbohydrate: number }, column: Object): number {
    return data.Protein * 4 + data.Fat * 9 + data.Carbohydrate * 4;
};

```

{% endtab %}

## Render boolean values as checkbox

To render boolean values as checkbox in columns, you need to set [`displayAsCheckBox`](../api/grid/column/#displayascheckbox) property as **true**.

{% tab template="grid/grid", es5Template="displayascheckbox" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid(
    {
        dataSource: data.slice(0,10),
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            {
                field: 'CustomerID', headerText: 'Customer ID', width: 150
            },
            { field: 'Freight', headerText: 'Freight', width: 100, textAlign: 'Right' },
            { field: 'ShipName', headerText: 'Ship Name', width: 180 },
            { field: 'Verified', headerText: 'Verified', width: 150, displayAsCheckBox: true }
        ],
        height: 315
    });
grid.appendTo('#Grid');

```

{% endtab %}

## See Also

* [How to Change Column Header Text Dynamically](./how-to/change-header-text-dynamically)
* [Customize Column Styles](./how-to/customize-column-styles)
* [Custom Tooltip for Columns](how-to/display-custom-tool-tip-for-columns-in-grid)
* [How to Render Other Component in a Column](how-to/render-other-components-in-column)
* [How to change the Orientation of Header Text](./how-to/change-orientation-of-header-text)
* [Group Column by Format](./grouping#group-by-format)
* [How to Use Edit Template in Foreign Key Column](./how-to/use-edit-template-in-foreign-key-column)
* [How to Create and use custom Filter UI in Foreign Key Column](./how-to/customize-filter-ui-in-foreign-key)
* [How to Use Filter Bar Template in Foreign Key Column](./how-to/use-filter-bar-template-in-foreign-key-column)
* [How to Perform aggregation in Foreign Key Column](./how-to/perform-aggregation-in-foreign-key-column)
* [How to set complex column as Foreignkey column](./how-to/complex-column-as-foreign-key-column)
* [Complex Data Binding with list of Array Of Objects](./how-to/list-of-array-of-objects)