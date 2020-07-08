---
title: "Customize Pager DropDown"
component: "Grid"
description: "Learn how to Customize Pager DropDown."
---

# Customize Pager DropDown

To customize the default values of pager drop-down, you need to define the [`pageSizes`](../../api/grid/pageSettings/#pagesizes) as array of strings.

{% tab template="grid/pagerdropdown",es5Template="pagerdropdown" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    pageSettings:{pageSizes: ["5", "10", "All"]},
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
});
grid.appendTo('#Grid');

```

{% endtab %}
