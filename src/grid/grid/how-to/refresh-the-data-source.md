---
title: "Refresh the Datasource"
component: "Grid"
description: "Learn how to refresh the Grid dataSource."
---

# Refresh the data source

You can add/delete the data source records through an external button. To reflect the data source changes in the grid, invoke the [`refresh`](../../api/grid/#refresh) method.

To refresh the data source:

**Step 1**:

Add/delete the data source record by using the following code.

```typescript
    grid.dataSource.unshift(data); // add a new record.

    grid.dataSource.splice(selectedRow, 1); // delete a record.

```

**Step 2**:

Refresh the grid after the data source change by using the [`refresh`](../../api/grid/#refresh) method.

```typescript
    grid.refresh(); // refresh the Grid.

```

{% tab template="grid/refresh-grid", sourceFiles="index.ts,index.css,index.html",es5Template="refresh" %}

```typescript

import { Grid } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 280
});
grid.appendTo('#Grid');

let add: Button = new Button({}, '#add');
let dele: Button = new Button({}, '#delete');

document.getElementById('add').onclick = () => {
    let data: Object = { OrderID: 10247, CustomerID: "ASDFG", Freight: 40.4, OrderDate: new Date(8367642e5) };
    (<Object[]>grid.dataSource).unshift(data); // add new record.
    grid.refresh(); // refresh the Grid.
};

document.getElementById('delete').onclick = () => {
    if (grid.getSelectedRowIndexes().length) {
        let selectedRow: number = grid.getSelectedRowIndexes()[0];
        (<Object[]>grid.dataSource).splice(selectedRow, 1); // delete the selected record.
    } else {
        alert("No records selected for delete operation");
    }
    grid.refresh(); // refresh the Grid.
};

```

{% endtab %}
