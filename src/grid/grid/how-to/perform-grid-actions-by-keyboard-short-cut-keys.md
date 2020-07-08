---
title: "Perform Grid actions by keyboard shortcut keys"
component: "Grid"
description: "Learn how to Perform Grid actions by keyboard shortcut keys."
---

# Perform Grid actions by keyboard shortcut keys

Using keyboard shortcuts, Grid performs navigation and actions.

In addition, You can also perform grid actions with custom keyboard shortcuts. This operation has to be achieved outside of the grid with the help of `keydown` event.

The following example demonstrates on `Adding` a new row when `Enter` key is pressed in the grid.

{% tab template="grid/grid",es5Template="keyboard-actions" %}

```typescript
import { Grid, Edit, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true},
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true }},
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

grid.element.addEventListener("keydown", keyDownHandler);

function keyDownHandler(e: any): void {
    if(e.keyCode === 13 ) {
        let gridIns: any = document.getElementById("Grid").ej2_instances[0];
        gridIns.addRecord();
    }
}

```

{% endtab %}
