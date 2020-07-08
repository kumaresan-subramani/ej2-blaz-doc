---
title: "Hierarchical Binding"
component: "Grid"
description: "Learn how to display master-detail data in the Essential JS 2 DataGrid control in a hierarchical manner."
---

# Hierarchical Binding

The Grid allows display of table data in a hierarchical structure to visualize relations between parent and child records. This feature is enabled by defining the [`childGrid`](../api/grid/#childgrid) and
[`childGrid.queryString`](../api/grid/#querystring). The [`childGrid`](../api/grid/#childgrid) describes the options of grid and the [`childGrid.queryString`](../api/grid/#querystring) describes the relation between parent and child grids.

To use hierarchical binding, inject the [`DetailRow`](../api/grid/detailRow) module in the grid.

{% tab template="grid/grid",es5Template="hierarchicalbinding" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { employeeData } from './employeeData.ts';

Grid.Inject(DetailRow);

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
    },
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

> * Grid supports n level of child grids.
> * Hierarchical binding is not supported when [`DetailTemplate`](../api/grid/#detailtemplate) is enabled.

## ExpandAll by external button

By default, grid renders in collapsed state. You can expand all child grid rows by invoking the [`expandAll`](../api/grid/detailRow/#expandall) method, and collapse all grid rows by invoking the [`collapseAll`](../api/grid/detailRow/#collapseall) through an external button.

{% tab template="grid/hierarchy-method",es5Template="expandall" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { data, employeeData } from './datasource.ts';

Grid.Inject(DetailRow);

let expandBtn: Button = new Button();
expandBtn.appendTo('#expandall');

let collapseBtn: Button = new Button();
collapseBtn.appendTo('#collapseall');

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
    },
    height: 265
});
grid.appendTo('#Grid');

document.getElementById('expandall').addEventListener('click', () => {
    grid.detailRowModule.expandAll();
});
document.getElementById('collapseall').addEventListener('click', () => {
    grid.detailRowModule.collapseAll();
});

```

{% endtab %}

## Expand child grid initially

You can expand a particular child grid at initial rendering by invoking the [`expand`](../api/grid/detailRow/#expand) method in the [`dataBound`](../api/grid/#databound) event.

{% tab template="grid/grid",es5Template="expandchild" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { employeeData } from './employeeData.ts';

Grid.Inject(DetailRow);

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
    },
    height: 315,
    dataBound: onDataBound
});
grid.appendTo('#Grid');

function onDataBound(): void {
    this.detailRowModule.expand(1); // initial expand 1 chid Grid.
}

```

{% endtab %}

## Dynamically load child grid data

You can dynamically load child grid dataSource by using the [`load`](../api/grid#load) event.
This [`load`](../api/grid#load) event triggers when the child grid is expanded for the first time.

{% tab template="grid/grid",es5Template="dynamicchild" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { employeeData } from './employeeData.ts';

Grid.Inject(DetailRow);

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
        load: onLoad
    },
    height: 315
});
grid.appendTo('#Grid');

function onLoad(args: Object): void {
    this.dataSource = data; // assign data source for child grid.
}

```

{% endtab %}

## Bind hierarchy grid with different field

By default, Parent and child grid relation will be maintained by `queryString` property. We should use the same field name to map both parent and child grid. To achieve parent and child relation with different fields, we need to change the mapping value in the child grid [`load`](../api/grid/#load) event.

In the below sample, we have bound the child and parent grid with different fields. Parent grid field name as `EmployeeID` and the child grid field name as `ID`. We need to define the mapping value of `parentKeyFieldValue` from the parent row data in the child grid `load` event.

{% tab template="grid/grid",es5Template="binddifferentfield" %}

```typescript
import { Grid, DetailRow } from '@syncfusion/ej2-grids';
import { data } from './childdata.ts';
import { employeeData } from './employeeData.ts';

Grid.Inject(DetailRow);

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        dataSource: data,
        queryString: 'ID',
        columns: [
            { field: 'ID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
        load: onLoad,
    },
    height: 315
});
grid.appendTo('#Grid');

function onLoad(): void {
  this.parentDetails.parentKeyFieldValue = this.parentDetails.parentRowData['EmployeeID'];
}

```

{% endtab %}

## Adding Record in ChildGrid

Parent and child grid are related by [`queryString`](../api/grid/#querystring) field value.
To maintain this relation in newly added record, You need to set value for [`queryString`](../api/grid/#querystring) field in the added data
by the [`actionBegin`](../api/grid/#actionbegin) event.

In the below demo, `EmployeeID` field relates the parent and child grids. To add a new record in child grid, We have to set the `EmployeeID` field
with parent record's [`queryString`](../api/grid/#querystring) field value in the [`actionBegin`](../api/grid/#actionbegin) event.

{% tab template="grid/grid",es5Template="querystring" %}

```typescript
import { Grid, DetailRow, AddEventArgs, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { employeeData } from './employeeData.ts';

Grid.Inject(DetailRow, Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: employeeData,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
        columns: [
            { field: 'OrderID', headerText: 'Order ID', isPrimaryKey:true, textAlign: 'Right', width: 120 },
            { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', allowEditing:false, width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ],
        actionBegin: actionBegin
    },
    height: 315
});
grid.appendTo('#Grid');

function actionBegin(args: AddEventArgs): void {
    if (args.requestType === "add") {
        // `parentKeyFieldValue` refers to the queryString field value of the parent record.
       args.data.EmployeeID = this.parentDetails.parentKeyFieldValue;
    }
}

```

{% endtab %}
