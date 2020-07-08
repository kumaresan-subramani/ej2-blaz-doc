---
title: "Select grid rows based on certain condition"
component: "Grid"
description: "Learn how to select rows in grid based on certain condition"
---

# Select grid rows based on certain condition

You can select the specific row in the grid based on a certain condition by using the [`selectRows`](../../api/grid/#selectrows) method in the [`dataBound`](../../api/grid/#databound) event of Grid.

In the below demo, we have selected the grid rows only when `EmployeeID` column value greater than `3`.

{% tab template="grid/databasedselect",es5Template="databasedselect" %}

```typescript
import { Grid, Selection, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Selection, Page);

let selIndex: any = [];
let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    selectionSettings: {type: "Multiple"},
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    rowDataBound: function(args) {
        if (args.data['EmployeeID'] > 3) {
            selIndex.push(parseInt(args.row.getAttribute('aria-rowindex')));
        }
    },
    dataBound: function(args) {
        if (selIndex.length) {
            this.selectRows(selIndex);
            selIndex = [];
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}