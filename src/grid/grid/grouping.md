---
title: "Grouping"
component: "Grid"
description: "Learn how to group rows, apply initial groups, customize caption templates, and group by format in the Essential JS 2 DataGrid control."
---

# Grouping

The Grid has options to group records by dragging and dropping the column header to the group drop area. When grouping is applied, grid records are organized into a hierarchical structure to facilitate easier expansion and collapse of records.

To enable grouping in the grid, set the [`allowGrouping`](../api/grid/#allowgrouping) as true. Grouping options can be configured through the [`groupSettings`](../api/grid/groupSettings). To group, inject the [`Group`](../api/grid/group) module in the grid.

{% tab template="grid/grid",es5Template="grouping" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 267
});
grid.appendTo('#Grid');

```

{% endtab %}

> * You can group and ungroup columns by using the [`groupColumn`](../api/grid/group/#groupcolumn) and
[`ungroupColumn`](../api/grid/group/#ungroupcolumn) methods.
> * To disable grouping for a particular column, set the
[`columns.allowGrouping`](../api/grid/column/#allowgrouping) to false.

## Initial group

To apply group at initial rendering, set the column field name in the `groupSettings.columns`.

{% tab template="grid/grid",es5Template="initgroup" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    groupSettings: { columns: ['CustomerID', 'ShipCity'] },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 267
});
grid.appendTo('#Grid');

```

{% endtab %}

## Caption template

You can customize the group caption by using the [`groupSettings.captionTemplate`](../api/grid/column/#captionTemplate) property.

{% tab template="grid/captiontemplate", sourceFiles="index.ts,index.html",es5Template="template" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: employeeData,
    allowGrouping: true,
    groupSettings: { captionTemplate: '#captiontemplate', columns: ['EmployeeID'] },
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID' },
        { field: 'CustomerID', headerText: 'Customer ID' },
        { field: 'FirstName', headerText: 'Name', width: 120 },
        { field: 'Title', headerText: 'Title', width: 170 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Add Custom text using caption template

You can customize the group caption text by using the [`groupSettings.captionTemplate`](../api/grid/column/#captionTemplate) property.

{% tab template="grid/customText-captiontemplate", sourceFiles="index.ts,index.html",es5Template="template" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { employeeData } from './datasource.ts';

Grid.Inject(Group);
let grid: Grid = new Grid({
    dataSource: employeeData,
    allowGrouping: true,
    groupSettings: { captionTemplate: '#captiontemplate', columns: ['EmployeeID'] },
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID' },
        { field: 'CustomerID', headerText: 'Customer ID' },
        { field: 'FirstName', headerText: 'Name', width: 120 },
        { field: 'Title', headerText: 'Title', width: 170 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Hide drop area

To avoid ungrouping or further grouping of a column after initial column
grouping, define the [`groupSettings.showDropArea`](../api/grid/groupSettings/#showdroparea) as false.

{% tab template="grid/grid",es5Template="hidedroparea" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    groupSettings: { showDropArea: false, columns: ['CustomerID', 'ShipCity'] },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Group with paging

On grouping columns with paging feature, the aggregated information and total items are displayed based on the current page. The grid does not consider aggregated information and total items from other pages. To get additional details (aggregated information and total items) from other pages, set the [`groupSettings.disablePageWiseAggregates`](../api/grid/groupSettings/#disablePageWiseAggregates) to false.

> If remote data is bound to grid dataSource, two requests will be sent when performing grouping action; one for getting the grouped data and another for getting aggregate details and total items count.

## Group by format

By default, a column will be grouped by the data or value present for the particular row. To group the numeric
or datetime column based on the mentioned format, you have to enable the
[`enableGroupByFormat`](../api/grid/column/#enablegroupbyformat) property of the corresponding
grid columns.

{% tab template="grid/grid",es5Template="groupformat" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    groupSettings: { showDropArea: false, columns: ['OrderDate', 'Freight'] },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'OrderDate', headerText: 'Order Date', format: 'yMMM', enableGroupByFormat: true, width: 150 },
        { field: 'Freight', headerText: 'Freight', format: 'C2', enableGroupByFormat: true, width: 150 }
    ],
    height: 315
});
grid.appendTo('#Grid');

```

{% endtab %}

## Grouping events

During the group action, the grid component triggers two events. The [`actionBegin`](../api/grid/#actionbegin) event
triggers before the group action starts and the [`actionComplete`](../api/grid/#actioncomplete) event triggers after the group action is completed. Using these events you can perform any action.

{% tab template="grid/grouping-event",es5Template="groupevent" %}

```typescript
import { Grid, Group, ActionEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 260,
    actionBegin: actionHandler,
    actionComplete: actionHandler
});
grid.appendTo('#Grid');

function actionHandler(args: ActionEventArgs) {
    alert(args.requestType + ' ' + args.type); //Custom Action
}

```

{% endtab %}

> The [`args.requestType`](../api/grid/sortEventArgs/#requesttype) is based on the current action name. For example, when grouping, the [`args.requestType`](../api/grid/sortEventArgs/#requesttype) value will be 'grouping'.

## Collapse by external button

You can collapse the selected group from an external button by invoking the [`expandCollapseRows`](../api/grid/group/#expandcollapserows) method.

{% tab template="grid/grouping-collapse",es5Template="external" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    groupSettings: { columns: ['ShipCity'] },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 240
});
grid.appendTo('#Grid');

let collapse: Button = new Button({ cssClass: 'e-flat' }, '#collapse');

document.getElementById('collapse').addEventListener('click', () => {
    if (grid.getSelectedRowIndexes().length) {
        let currentTr: Element = grid.getRows()[grid.getSelectedRowIndexes()[0]];
        while (currentTr.classList && currentTr.classList.length) {
            currentTr = <Element>currentTr.previousSibling;
        }
        let collapseElement = currentTr.querySelector('.e-recordplusexpand');
        grid.groupModule.expandCollapseRows(collapseElement); //Pass the collapse row element.
    }
});

```

{% endtab %}

## Reordering on Grouped Columns

Grid provides an option to interchange the position of the Grouped Columns by dragging and dropping the grouped headercells in the droparea. So, any new column entering into the droparea can also be dropped in any position.

To enable this feature, you have to set the [`groupSettings.allowReordering`](../api/grid/groupSettings/#allowReordering) property as **true**.

{% tab template="grid/grouping-animation",es5Template="external" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowGrouping: true,
    groupSettings: { columns: ['ShipCity'], allowReordering: true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 240
});
grid.appendTo('#Grid');

```

{% endtab %}

## See Also

* [Exporting grouped records](./excel-exporting#Exporting-grouped-records)