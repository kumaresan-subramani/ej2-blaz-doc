---
title: "Display custom tooltip for columns in grid"
component: "Grid"
description: "Learn how to display custom tooltip for columns in grid."
---

# Display custom tooltip for columns in grid

To display custom ToolTip ([`EJ2 Tooltip`](../../../tooltip/getting-started)),  use the
[`queryCellInfo`](../../api/grid/#querycellinfo) event.

Render the ToolTip component for the grid cells by using the following code in the [`queryCellInfo`](../../api/grid/#querycellinfo) event.

```typescript
function tooltip (args: QueryCellInfoEventArgs) {
    let tooltip: Tooltip = new Tooltip({
        content: args.data[args.column.field].toString();
    }, args.cell);
}

```

{% tab template="grid/custom-tooltip",es5Template="tooltip" %}

```typescript
import { Grid, QueryCellInfoEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Tooltip } from '@syncfusion/ej2-popups';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 140 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    queryCellInfo: tooltip,
    height: 315
});
grid.appendTo('#Grid');

function tooltip(args: QueryCellInfoEventArgs): void { // event triggers on every cell render.
    let tooltip: Tooltip = new Tooltip({
        content: args.data[args.column.field].toString() // add Essential JS2 tooltip for every cell.
    }, <HTMLElement>args.cell);
}

```

{% endtab %}
