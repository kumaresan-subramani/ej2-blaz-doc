---
title: "Exporting Grid in Cordova application"
component: "Grid"
description: "Learn how to export Grid in Cordova application."
---

# Exporting Grid in Cordova application

Cordova application does not support direct file download. So we have to use the Blob stream to export the Grid.
You can use corresponding exporting methods and exportComplete events to get the Blob stream.

{% tab template="grid/exporting-blob-data", es5Template="export-blob-data" %}

```typescript
import { EmitType } from '@syncfusion/ej2-base'
import { Grid, Page, Toolbar, ExcelExport, ExcelExportCompleteArgs, PdfExport, PdfExportCompleteArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page, Toolbar, ExcelExport, PdfExport);
/**
 * Exporting Blob data
 */

let excelExpComplete: EmitType<ExcelExportCompleteArgs> = (args: ExcelExportCompleteArgs) => {
        //This event will be triggered when excel exporting.
            args.promise.then((e: { blobData: Blob }) => {
        //In this `then` function, we can get blob data through the arguments after promise resolved.
                exportBlob(e.blobData);
    });
};
let pdfExpComplete: EmitType<PdfExportCompleteArgs> = (args: PdfExportCompleteArgs) => {
    //This event will be triggered when pdf exporting.
        args.promise.then((e: { blobData: Blob }) => {
        //In this `then` function, we can get blob data through the arguments after promise resolved.
        exportBlob(e.blobData);
    });
};


let exportBlob: Function = (blob: Blob) => {
    let a: HTMLAnchorElement = document.createElement('a');
    document.body.appendChild(a);
    a.style.display = 'none';
    let url: string = window.URL.createObjectURL(blob);
    a.href = url;
    a.download = 'Export';
    a.click();
    window.URL.revokeObjectURL(url);
    document.body.removeChild(a);
}

let grid: Grid = new Grid(
    {
        dataSource: data,
        allowExcelExport: true,
        allowPdfExport: true,
        excelExportComplete: excelExpComplete,
        pdfExportComplete: pdfExpComplete,
        toolbar: ['PdfExport','ExcelExport'],
        columns: [
            {
                field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 90
            },
            {
                field: 'CustomerID', headerText: 'Customer ID', width: 90
            },
            { field: 'ShipCountry', headerText: 'ShipCountry', width: 90 },
        ]
    });
grid.appendTo('#Grid');
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_pdfexport') {
        grid.pdfExport(null, null, null, true);
    }
    if (args['item'].id === 'Grid_excelexport') {
        grid.excelExport(null, null, null, true);
    }

}

```

{% endtab %}
