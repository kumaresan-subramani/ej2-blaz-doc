---
title: "Display null date values at always"
component: "Grid"
description: "Learn how to display null date values at always."
---

# Display the null date values at bottom of the Grid while perform sorting

By default the null values are displayed at bottom of the Grid row while perform sorting in ascending order. As well as this values are displayed at top of the Grid row while perform sorting with descending order. But you can customize this default order to display the null values at always bottom row of the Grid by using[`column.sortComparer`](../../api/grid/column/#sortcomparer) method.

In the below demo we have displayed the null values at bottom of the Grid row while sorting the **OrderDate** column in both ways.

{% tab template="grid/sort-comparer", es5Template="sortComparer" %}

```typescript
import { Grid, Sort, Page, SortEventArgs  } from '@syncfusion/ej2-grids';
import { OrderData } from './datasource.ts';

Grid.Inject(Sort, Page);
let grid: Grid = new Grid({
    dataSource: OrderData,
    allowSorting: true,
    actionBegin: actionBegin,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'OrderDate', headerText: 'Order Date', format: 'yMd', sortComparer: sortComparer, width: 120},
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265
});

let action: string;
function actionBegin(args: SortEventArgs) {
        if (args.requestType === 'sorting') {
            action = args.direction;
        }
}

function sortComparer(reference, comparer) {
        const sortAsc = action === 'Ascending' ? true : false;
        if (sortAsc && reference === null) {
            return 1;
        } else if (sortAsc && comparer === null) {
            return -1;
        } else if (!sortAsc && reference === null) {
            return -1;
        } else if (!sortAsc && comparer === null) {
            return 1;
        } else {
            return reference - comparer;
        }
}
grid.appendTo('#Grid');
```

{% endtab %}