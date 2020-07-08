---
title: "Change Column Header Text Dynamically"
component: "Grid"
description: "Learn how to change column header text dynamically."
---

# Change Column Header Text Dynamically

You can change the column [`headerText`](../../api/grid/column/#headertext) dynamically through an external button.

Follow the given steps to change the header text dynamically:

**Step 1**:

Get the column object corresponding to the field name by using the [`getColumnByField`](../../api/grid/#getcolumnbyfield) method.
Then, change the header text value.

```typescript
let column = grid.getColumnByField("ShipCity"); // Get column object.
column.headerText = 'Changed Text';

```

**Step 2**:

To reflect the changes in the grid header, invoke the [`refreshHeader`](../../api/grid/#refreshheader) method.

```typescript
grid.refreshHeader();

```

{% tab template="grid/change-header-text", sourceFiles="index.ts,index.css,index.html",es5Template="dynamic" %}

```typescript
import { Grid, Column } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 100 }
    ],
    height: 280
});
grid.appendTo('#Grid');

let btn: Button = new Button({ cssClass: 'e-flat' }, '#change-text');

document.getElementById('change-text').addEventListener('click', () => { // changing the header text for ShipCity column.
    let column: Column = grid.getColumnByField("ShipCity"); // get the JSON object of the column corresponding to the field name.
    column.headerText = "Changed Text"; // assign a new header text to the column.
    grid.refreshHeader();
});

```

{% endtab %}
