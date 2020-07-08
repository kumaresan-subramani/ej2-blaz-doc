---
title: "Passing additional parameters to the server when Exporting"
component: "Grid"
description: "Learn how to pass additional parameters to server when Exporting."
---

# Passing additional parameters to the server when Exporting

You can pass the additional parameter in the `query` property by invoking `addParams` method. In the `toolbarClick` event, you can define params as key and value pair so it will receive at the server side when exporting.

In the below example, we have passed `recordcount` as `12` using `addParams` method.

{% tab template="grid/grid",es5Template="addparams-exporting" %}

```typescript

import { Grid, Page, Toolbar, PdfExport, ExcelExport } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Query } from '@syncfusion/ej2-data';

Grid.Inject(Page, Toolbar, PdfExport, ExcelExport);

let queryClone: Object;
let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowPdfExport: true,
    allowExcelExport: true,
    toolbar: ['PdfExport', 'ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', visible: false },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'ShipCity', headerText: 'ShipCity', textAlign: 'Right', width: 140 }
    ],
    height: 230
});
grid.appendTo('#Grid');
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_pdfexport') {
        queryClone = grid.query;
        grid.query = new Query().addParams("recordcount", "12");
        grid.pdfExport();
    }
    if (args['item'].id === 'Grid_excelexport') {
        queryClone = grid.query;
        grid.query = new Query().addParams("recordcount", "12");
        grid.excelExport();
    }
}
grid.pdfExportComplete = () => {
        grid.query = queryClone;
    }
grid.excelExportComplete = () => {
        grid.query = queryClone;
    }

```

{% endtab %}