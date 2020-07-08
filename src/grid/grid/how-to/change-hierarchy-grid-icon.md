---
title: "How to change icon of Hierarchy grid"
component: "Grid"
description: "Learn how to change the icon of Hierarchy grid in the Essential JS 2 DataGrid control."
---

# How to Change icon in Hierarchy grid

You can change default expand/collapse icon of the Hierarchy Grid by using custom Css.

You can change the content code of the corresponding icon which you want.

To use hierarchical binding, inject the [`DetailRow`](../api/grid/detailRow) module in the grid.

**Css**:

Use the below css in your `index.html` file.

```css
    .e-grid .e-icon-grightarrow::before,
        .e-grid-menu .e-icon-grightarrow::before {
            content: '\e7f9';
        }
    .e-grid .e-icon-gdownarrow::before,
        .e-grid-menu .e-icon-gdownarrow::before {
            content: '\e934';
        }

```

In this below demo, we have changed the expand/collapse icon to Plus/Minus icon.

{% tab template="grid/changeicon", es5Template="icon" %}

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