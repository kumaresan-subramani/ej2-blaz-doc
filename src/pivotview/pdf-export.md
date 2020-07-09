---
title: "PDF Exporting"
component: "Pivot Table"
description: "Export pivot table data to PDF document."
---

# PDF Export

PDF export allows exporting pivot table data as PDF document. To enable PDF export in the pivot table, set the `allowPdfExport` as true. You need to use the `pdfExport` method for PDF exporting.

{% tab template="pivot-table/pdf-export", es5Template="export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    pivotTableObj.pdfExport();
};

```

{% endtab %}

## Multiple pivot table exporting

PDF export provides an option for exporting multiple pivot tables to same file. In this exported document, each pivot table will be exported to new page of document in same file.

{% tab template="pivot-table/pdf-export", es5Template="multiple-export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
let pivotTableObj2: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        rows: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        columns: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 280
});
pivotTableObj.appendTo('#PivotTable');
pivotTableObj2.appendTo('#PivotTable2');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    let firstGridPdfExport: Promise<Object> = pivotTableObj.grid.pdfExport({}, true);
    firstGridPdfExport.then((pdfData: Object) => {
        pivotTableObj2.pdfExport({}, false, pdfData);
    });
};

```

{% endtab %}

## Customization during PDF export

PDF export provides option to customize mapping of pivot table to the exported PDF document.

### To add header and footer

You can customize text, page number, line, page size and changing orientation in header and footer.

#### How to write a text in header/footer

You can add text either in header or footer of the exported PDF document like in the below code example.

```typescript

let pdfExportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'Text',
                value: "Northwind Traders",
                position: { x: 0, y: 50 },
                style: { textBrushColor: '#000000', fontSize: 13 }
            },

        ]
    }
}

```

#### How to draw a line in header/footer

You can add line either in header or footer of the exported PDF document like in the below code example.

Supported line styles:
* dash
* dot
* dashdot
* dashdotdot
* solid

```typescript

let pdfExportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'Line',
                style: { penColor: '#000080', penSize: 2, dashStyle: 'Solid' },
                points: { x1: 0, y1: 4, x2: 685, y2: 4 }
            }
        ]
    }
}

```

#### Add page number in header/footer

You can add page number either in header or footer of exported PDF document like in the below code example.

Supported page number types:
* LowerLatin - a, b, c,
* UpperLatin - A, B, C,
* LowerRoman - i, ii, iii,
* UpperRoman - I, II, III,
* Number - 1,2,3.

```typescript

 let pdfExportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'PageNumber',
                pageNumberType: 'Arabic',
                format: 'Page {$current} of {$total}', //optional
                position: { x: 0, y: 25 },
                style: { textBrushColor: '#ffff80', fontSize: 15, hAlign: 'Center' }
            }
        ]
    }
}

```

The below code illustrates the PDF export customization options.

{% tab template="pivot-table/pdf-export", es5Template="header-footer", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { PdfExportProperties } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    let pdfExportProperties: PdfExportProperties = {
        header: {
            fromTop: 0,
            height: 130,
            contents: [
                {
                    type: 'Text',
                    value: "Pivot Table",
                    position: { x: 0, y: 50 },
                    style: { textBrushColor: '#000000', fontSize: 13, dashStyle:'Solid',hAlign:'Center' }
                }
            ]
        },
        footer: {
            fromBottom: 160,
            height: 150,
            contents: [
                {
                    type: 'PageNumber',
                    pageNumberType: 'Arabic',
                    format: 'Page {$current} of {$total}',
                    position: { x: 0, y: 25 },
                    style: { textBrushColor: '#02007a', fontSize: 15 }
                }
            ]
        }
    };
    pivotTableObj.pdfExport(pdfExportProperties);
};

```

{% endtab %}

### To change page orientation

Page orientation can be changed to "Landscape" (by default it's "Portrait") for the exported document using `PdfExportProperties`.

{% tab template="pivot-table/pdf-export", es5Template="page-layout", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { PdfExportProperties } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    let pdfExportProperties: PdfExportProperties = {
        pageOrientation: 'Landscape'
    };
    pivotTableObj.pdfExport(pdfExportProperties);
};

```

{% endtab %}

### To change page size

Page size can be customized for the exported document using `PdfExportProperties`.
Supported page sizes are:
* Letter
* Note
* Legal
* A0
* A1
* A2
* A3
* A5
* A6
* A7
* A8
* A9
* B0
* B1
* B2
* B3
* B4
* B5
* Archa
* Archb
* Archc
* Archd
* Arche
* Flsa
* HalfLetter
* Letter11x17
* Ledger

{% tab template="pivot-table/pdf-export", es5Template="page-size", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { PdfExportProperties } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    let pdfExportProperties: PdfExportProperties = {
        pageSize: 'Letter'
    };
    pivotTableObj.pdfExport(pdfExportProperties);
};

```

{% endtab %}

### Theme

PDF export provides an option to include theme for exported PDF document.

To apply theme in exported PDF, define the `theme` in `PdfExportProperties`.

> By default, material theme is applied to exported PDF document.

{% tab template="pivot-table/pdf-export", es5Template="theme-export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { PdfExportProperties } from '@syncfusion/ej2-grids';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    let pdfExportProperties: PdfExportProperties = {
        theme: {
            header: {
                fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true, borders: { color: '#64FA50', lineStyle: 'Thin' }
            },
            record: {
                fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true
            },
            caption: {
                fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true
            }
        }
    };
    pivotTableObj.pdfExport(pdfExportProperties);
};

```

{% endtab %}

## Virtual Scroll Data

You can export the pivot table virtual scroll data as PDF document by using PivotEngine export without any performance degradation. To enable PivotEngine export in the pivot table, set the `allowPdfExport` as true. You need to use the `exportToPDF` method for PivotEngine export.

> To use PivotEngine export, You need to inject the `PDFExport` module in pivot table.
> PivotEngine export will be performed while enabling virtual scrolling by default

{% tab template="pivot-table/pdf-export", es5Template="engine-export", sourceFiles="index.ts,index.html" %}

```typescript

import { PivotView, IDataSet, PDFExport } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(PDFExport);

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    pivotTableObj.pdfExportModule.exportToPDF();
};

```

{% endtab %}

### Repeat row headers

Repeat row headers on each page can be achieved using PivotEngine export option. To disable repeat row headers, you need to set `allowRepeatHeader` to **false** in beforeExport event. You need to use the `exportToPDF` method for PivotEngine export.

> To use PivotEngine export, You need to inject the `PDFExport` module in pivot table.
> By default, repeat row headers is enabled in the PivotEngine export.

{% tab template="pivot-table/pdf-export", es5Template="repeat-header", sourceFiles="index.ts,index.html" %}

```typescript

import { PivotView, IDataSet, PDFExport, BeforeExportEventArgs } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(PDFExport);

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    beforeExport: function(args: BeforeExportEventArgs) {
        args.allowRepeatHeader = false;
    },
    allowPdfExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#pdf');

document.getElementById('pdf').onclick = function () {
    pivotTableObj.pdfExportModule.exportToPDF();
};

```

{% endtab %}

## See Also

* [Excel Exporting](./excel-export)