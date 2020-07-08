---
title: "Add a title to the data grid when using Grid print action"
component: "Grid"
description: "Learn how to add a header while Grid printing in the Essential JS 2 DataGrid control."
---

# Add a title to the header when using Grid print function

You can add your title in the header through an [`beforePrint`](../../api/grid/#beforeprint) event. With the help of this event you can add your title element as you want.

{% tab template="grid/titleprint", es5Template="refresh" %}

```typescript
import { Grid, Page, Toolbar } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    beforePrint: beforePrint,
    toolbar: ['Print'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'OrderDate', headerText: 'Order Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ],
    height: 220
});
grid.appendTo('#Grid');

function beforePrint(args) {
    var div = document.createElement("Div")
        div.innerHTML = "Title here"
        div.style.textAlign = 'center';
        div.style.color = 'red';
        div.style.padding = '10px 0';
        div.style.fontSize = '25px';
        args.element.insertBefore(div, args.element.childNodes[0]);
}

```

{% endtab %}