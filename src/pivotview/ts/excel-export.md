---
title: "Excel Exporting"
component: "Pivot Table"
description: "Export pivot table data to Excel document."
---

# Excel Export

The Excel export allows pivot table data to export as Excel document. To enable Excel export in the pivot table, set the `allowExcelExport` as **true**. You need to use the `excelExport` method for Excel exporting.

{% tab template="pivot-table/excel-export", es5Template="export", sourceFiles="index.ts,index.html" %}

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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    pivotTableObj.excelExport();
}

```

{% endtab %}

## Multiple pivot table exporting

The Excel export provides an option to export multiple pivot table data in the same Excel file.

### Same WorkSheet

The Excel export provides support to export multiple pivot tables in same sheet. To export in same sheet, define `multipleExport.type` as `AppendToSheet` in `ExcelExportProperties`. It has an option to provide blank rows between pivot tables and these blank row(s) count can be defined using the`multipleExport.blankRows` property.

>By default, `multipleExport.blankRows` value is 5 between pivot tables within the same sheet.

{% tab template="pivot-table/excel-export", es5Template="samesheet-export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';
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
    allowExcelExport: true,
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
    allowExcelExport: true
});
pivotTableObj.appendTo('#PivotTable');
pivotTableObj2.appendTo('#PivotTable2');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    let excelExportProperties: ExcelExportProperties = {
        multipleExport: { type: 'AppendToSheet', blankRows: 2 }
    };
    let firstGridExport: Promise<any> = pivotTableObj.grid.excelExport(excelExportProperties, true);
    firstGridExport.then((fData: any) => {
        pivotTableObj2.excelExport(excelExportProperties, false, fData);
    });
};

```

{% endtab %}

### New WorkSheet

Excel export provides support to export multiple pivot tables into new sheets. To export in new sheets, define  `multipleExport.type` as `NewSheet` in `ExcelExportProperties`.

{% tab template="pivot-table/excel-export", es5Template="newsheet-export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';
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
    allowExcelExport: true,
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
    allowExcelExport: true
});
pivotTableObj.appendTo('#PivotTable');
pivotTableObj2.appendTo('#PivotTable2');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    let excelExportProperties: ExcelExportProperties = {
        multipleExport: { type: 'NewSheet' }
    };
    let firstGridExport: Promise<any> = pivotTableObj.grid.excelExport(excelExportProperties, true);
    firstGridExport.then((fData: any) => {
        pivotTableObj2.excelExport(excelExportProperties, false, fData);
    });
};

```

{% endtab %}

## Changing the pivot table style while exporting

The Excel export provides an option to change colors for headers, caption and records in pivot table before exporting. In-order to apply colors, define **theme** settings in **excelExportProperties** object and pass it as a parameter to the [`excelExport`](https://ej2.syncfusion.com/documentation/api/pivotview#excelexport) method.

>By default, material theme is applied to exported Excel document.

{% tab template="pivot-table/excel-export", es5Template="theme-export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';
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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    let excelExportProperties: ExcelExportProperties = {
        theme:
        {
            header: { fontName: 'Segoe UI', fontColor: '#666666' },
            record: { fontName: 'Segoe UI', fontColor: '#666666' },
            caption: { fontName: 'Segoe UI', fontColor: '#666666' }
        }
    };
    pivotTableObj.excelExport(excelExportProperties);
};

```

{% endtab %}

## Add header and footer while exporting

The Excel export provides an option to include header and footer content for the excel document before exporting. In-order to add header and footer, define **header** and **footer** properties in **excelExportProperties** object and pass it as a parameter to the [`excelExport`](https://ej2.syncfusion.com/documentation/api/pivotview#excelexport) method.

{% tab template="pivot-table/excel-export", es5Template="header-footer", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';
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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    let excelExportProperties: ExcelExportProperties = {
        header: {
            headerRows: 2,
            rows: [
                { cells: [{ colSpan: 4, value: "Pivot Table", style: { fontColor: '#C67878', fontSize: 20, hAlign: 'Center', bold: true, underline: true } }] }
            ]
        },
        footer: {
            footerRows: 4,
            rows: [
                { cells: [{ colSpan: 4, value: "Thank you for your business!", style: { hAlign: 'Center', bold: true } }] },
                { cells: [{ colSpan: 4, value: "!Visit Again!", style: { hAlign: 'Center', bold: true } }] }
            ]
        }
    };
    pivotTableObj.excelExport(excelExportProperties);
};

```

{% endtab %}

## Changing the file name while exporting

The Excel export provides an option to change file name of the document before exporting. In-order to change the file name, define **fileName** property in **excelExportProperties** object and pass it as a parameter to the [`excelExport`](https://ej2.syncfusion.com/documentation/api/pivotview#excelexport) method.

{% tab template="pivot-table/excel-export", es5Template="file-name", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';
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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    let excelExportProperties: ExcelExportProperties = {
        filename:'sample.xslx'
    };
    pivotTableObj.excelExport(excelExportProperties);
};

```

{% endtab %}

## CSV Export

Also, the Excel export allows pivot table data to be exported in `CSV` file format. To export pivot table in `CSV` file format, you need to use the `csvExport` method.

{% tab template="pivot-table/excel-export", es5Template="csv-export", sourceFiles="index.ts,index.html" %}

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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    pivotTableObj.csvExport();
}

```

{% endtab %}

## Virtual Scroll Data

You can export the pivot table virtual scroll data as Excel/CSV document by using PivotEngine export without any performance degradation. To enable PivotEngine export in the pivot table, set the `allowExcelExport` as true. You need to use the `exportToExcel` method for PivotEngine export.

> To use PivotEngine export, You need to inject the `ExcelExport` module in pivot table.
> PivotEngine export will be performed while enabling virtual scrolling by default.

### Virtual Scroll Data Excel Export

{% tab template="pivot-table/excel-export", es5Template="engine-export", sourceFiles="index.ts,index.html" %}

```typescript

import { PivotView, IDataSet, ExcelExport } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(ExcelExport);

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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    pivotTableObj.excelExportModule.exportToExcel('Excel');
};

```

{% endtab %}

### Virtual Scroll Data CSV Export

{% tab template="pivot-table/excel-export", es5Template="engine-csv-export", sourceFiles="index.ts,index.html" %}

```typescript

import { PivotView, IDataSet, ExcelExport } from '@syncfusion/ej2-pivotview';
import { Button } from '@syncfusion/ej2-buttons';
import { pivotData } from './datasource.ts';

PivotView.Inject(ExcelExport);

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
    allowExcelExport: true,
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#excel');

document.getElementById('excel').onclick = function () {
    pivotTableObj.excelExportModule.exportToExcel('csv');
};

```

{% endtab %}

## Events

### ExcelQueryCellInfo

The event `excelQueryCellInfo` triggers while framing each row and value cell during Excel export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `value` - It holds the cell value.
* `column` -  It holds column information for the current cell.
* `data` - It holds the entire row data across the current cell.
* `style`  - It holds the style properties for the cell.

{% tab template="pivot-table/pivot-table", es5Template="excel-querycell", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
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
    gridSettings: {
        excelQueryCellInfo: (args: ExcelQueryCellInfoEventArgs) => {
            //triggers every time for value cell while exporting
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

### ExcelHeaderQueryCellInfo

The event `excelHeaderQueryCellInfo` triggers on framing each header cell during Excel export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `cell` - It holds the current cell information.
* `style`  -  It holds the style properties for the cell.

{% tab template="pivot-table/pivot-table", es5Template="excel-header", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
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
    gridSettings: {
        excelHeaderQueryCellInfo: (args: ExcelHeaderQueryCellInfoEventArgs) => {
            //triggers every time for header cell while exporting
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');
```

{% endtab %}

## See Also

* [PDF Exporting](./pdf-export)