---
title: "Collapse all grouped rows at initial render"
component: "Grid"
description: "Learn how to collapse all grouped rows at initial render."
---

# Collapse all grouped rows at initial render

You can collapse all the grouped rows at initial rendering by using `dataBound` event with  `collapseAll` method of the grid.

In the below demo, all the grouped rows are collapsed at initial rendering.

{% tab template="grid/grid",es5Template="collapseall-init" %}

```typescript
import { Grid, Group } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group);

var initial = true;

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
    dataBound: bound,
    height: 267
});
grid.appendTo('#Grid');

function bound() {
    if(initial === true) {
        grid.groupModule.collapseAll();
        initial = false;
    }
}

```

{% endtab %}