---
title: "Migration"
component: "Grid"
description: "Learn how to migrate the EJ2 data grid from EJ1 Grid."
---

# Excel Export

The excel export allows exporting Grid data to Excel document. You need to use the
 [`excelExport`](../api/grid/#excelexport) method for exporting. To enable Excel export in the grid, set the [`allowExcelExport`](../api/grid/#allowexcelexport) as true.

To use excel export, You need to inject the `ExcelExport` module in grid.

{% tab template="grid/grid",es5Template="excelexport" %}

```typescript

import { Grid, Toolbar, ExcelExport, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        grid.excelExport();
    }
}
grid.appendTo('#Grid');

```

{% endtab %}

## Multiple Grid exporting

The excel export provides an option to export multiple grid data in the same excel file.

### Same sheet

The excel export provides support to export multiple grids in same sheet. To export in same sheet, define `multipleExport.type` as `AppendToSheet` in `exportProperties`. It have an option to provide blank rows between grids. These blank rows count can be defined by using the`multipleExport.blankRows`.

{% tab template="grid/export-mutiple-grid",es5Template="samesheet" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data, employeeData } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let firstGrid: Grid = new Grid({
    dataSource: data.slice(0, 5),
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ]
});
let secondGrid: Grid = new Grid({
    dataSource: employeeData.slice(0, 5),
    allowPaging: true,
    allowExcelExport: true,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'FirstName', width: 140, headerText: 'First Name', type: 'string' },
        { field: 'LastName', width: 140, headerText: 'Last Name', type: 'string' },
        { field: 'City', headerText: 'City', textAlign: 'Right', width: 120 },
        { field: 'BirthDate', headerText: 'Birth Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ]
});

firstGrid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'FirstGrid_excelexport') {
        let appendExcelExportProperties: ExcelExportProperties = {
            multipleExport: { type: 'AppendToSheet', blankRows: 2 }
        };

        let firstGridExport: Promise<any> = firstGrid.excelExport(appendExcelExportProperties, true);
        firstGridExport.then((fData: any) => {
            secondGrid.excelExport(appendExcelExportProperties, false, fData);
        });
    }

}
firstGrid.appendTo('#FirstGrid');
secondGrid.appendTo('#SecondGrid');


```

{% endtab %}

>By default, `multipleExport.blankRows` value is 5.

### New Sheet

Excel exporting provides support to export multiple grids in new sheet. To export in new sheet, define  `multipleExport.type` as `NewSheet` in `exportProperties`.

{% tab template="grid/export-mutiple-grid",es5Template="newsheet" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data, employeeData } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let firstGrid: Grid = new Grid({
    dataSource: data.slice(0, 5),
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ]
});
let secondGrid: Grid = new Grid({
    dataSource: employeeData.slice(0, 5),
    allowPaging: true,
    allowExcelExport: true,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'FirstName', width: 140, headerText: 'First Name', type: 'string' },
        { field: 'LastName', width: 140, headerText: 'Last Name', type: 'string' },
        { field: 'City', headerText: 'City', textAlign: 'Right', width: 120 },
        { field: 'BirthDate', headerText: 'Birth Date', textAlign: 'Right', width: 140, format: 'yMd' }
    ]
});

firstGrid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'FirstGrid_excelexport') {

        let appendExcelExportProperties: ExcelExportProperties = {
            multipleExport: { type: 'NewSheet' }
        };

        let firstGridExport: Promise<any> = firstGrid.excelExport(appendExcelExportProperties, true);
        firstGridExport.then((fData: any) => {
            secondGrid.excelExport(appendExcelExportProperties, false, fData);
        });
    }
}

firstGrid.appendTo('#FirstGrid');
secondGrid.appendTo('#SecondGrid');

```

{% endtab %}

## To customize excel export

The excel export provides an option to customize mapping of the grid to excel document.

### Export current page

The excel export provides an option to export the current page into excel. To export current page, define `exportType` to `CurrentPage`.

{% tab template="grid/grid",es5Template="exportcurrent" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page} from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        let excelExportProperties: ExcelExportProperties = {
            exportType: 'CurrentPage'
        };
        grid.excelExport(excelExportProperties);

    }
}
grid.appendTo('#Grid');

```

{% endtab %}

### Export hidden columns

The excel export provides an option to export hidden columns of grid by defining `includeHiddenColumn` as `true`.

{% tab template="grid/grid",es5Template="exporthide" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page)

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'ShipCountry', width: 140, headerText: 'Ship Country', visible: false },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        let excelExportProperties: ExcelExportProperties = {
            includeHiddenColumn: true
        };
        grid.excelExport(excelExportProperties);

    }
}
grid.appendTo('#Grid');

```

{% endtab %}

### Show or Hide columns on Exported Excel

You can show a hidden column or hide a visible column while printing the grid using [`toolbarClick`](../api/grid/#toolbarclick) and [`excelExportComplete`](../api/grid/#excelExportComplete) events.

In the `toolbarClick` event, based on `args.item.id` as `Grid_excelexport`. We can show or hide columns by setting `column.visible` property to `true` or `false` respectively.

In the excelExportComplete event, We have reversed the state back to the previous state.

In the below example, we have `CustomerID` as a hidden column in the grid. While exporting, we have changed `CustomerID` to visible column and `ShipCity` as hidden column.

{% tab template="grid/grid",es5Template="show-hide-excel" %}

```typescript

import { Grid, Toolbar, ExcelExport, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', visible: false },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'ShipCity', headerText: 'ShipCity', width: 140, textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        grid.columns[1].visible = false;
        grid.columns[3].visible = true;
        grid.excelExport();
    }
}
grid.pdfExportComplete = () => {
        grid.columns[1].visible = false;
        grid.columns[3].visible = true;
    }
grid.appendTo('#Grid');

```

{% endtab %}

### Conditional Cell Formatting

Grid cells in the exported Excel can be customized or formatted using [`excelQueryCellInfo`](../api/grid/#excelQueryCellInfo) event. In this event, we can format the grid cells of exported PDF document based on the column cell value.

In the below sample, we have set the background color for `Freight` column in the exported excel by `args.cell` and `backgroundColor` property.

{% tab template="grid/grid",es5Template="cell-format-excel" %}

```typescript

import { Grid, Toolbar, ExcelExport, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120 },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        grid.excelExport();
    }
}
grid.excelQueryCellInfo = (args: Object) => {
        if(args.column.field == 'Freight'){
            if(args.value < 30) {
                args.style = {backColor: '#99ffcc'};
            }
            else if(args.value < 60) {
                args.style = {backColor: '#ffffb3'};
            }
            else {
                args.style = {backColor: '#ff704d'};
            }
        }
    }
grid.queryCellInfo = (args: Object) => {
        if(args.column.field == 'Freight'){
            if(args.data['Freight'] < 30) {
                args.cell.bgColor = '#99ffcc';
            }
            else if(args.data['Freight'] < 60) {
                args.cell.bgColor = '#ffffb3';
            }
            else {
                args.cell.bgColor = '#ff704d';
            }
        }
    }
grid.appendTo('#Grid');

```

{% endtab %}

### Theme

The excel export provides an option to include theme for exported excel document.

To apply theme in exported Excel, define the `theme` in `exportProperties` .

{% tab template="grid/grid",es5Template="exceltheme" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        let excelExportProperties: ExcelExportProperties = {
            theme:
                {
                    header: { fontName: 'Segoe UI', fontColor: '#666666' },
                    record: { fontName: 'Segoe UI', fontColor: '#666666' },
                    caption: { fontName: 'Segoe UI', fontColor: '#666666' }
                }
        };
        grid.excelExport(excelExportProperties);

    }
}
grid.appendTo('#Grid');

```

{% endtab %}

>By default, material theme is applied to exported excel document.

### To add header and footer

The excel export provides an option to include header and footer content for exported excel document.

{% tab template="grid/grid",es5Template="exportfooter" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        let excelExportProperties: ExcelExportProperties = {
            header: {
                headerRows: 7,
                rows: [
                    { cells: [{ colSpan: 4, value: "Northwind Traders", style: { fontColor: '#C67878', fontSize: 20, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "2501 Aerial Center Parkway", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "Suite 200 Morrisville, NC 27560 USA", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "Tel +1 888.936.8638 Fax +1 919.573.0306", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, hyperlink: { target: 'https://www.northwind.com/', displayText: 'www.northwind.com' }, style: { hAlign: 'Center' } }] },
                    { cells: [{ colSpan: 4, hyperlink: { target: 'mailto:support@northwind.com' }, style: { hAlign: 'Center' } }] },
                ]
            },
            footer: {
                footerRows: 4,
                rows: [
                    { cells: [{ colSpan: 4, value: "Thank you for your business!", style: { hAlign: 'Center', bold: true } }] },
                    { cells: [{ colSpan: 4, value: "!Visit Again!", style: { hAlign: 'Center', bold: true } }] }
                ]
            },
        };

        grid.excelExport(excelExportProperties);

    }
}
grid.appendTo('#Grid');

```

{% endtab %}

### File Name for Exported document

You can assign the file name for the exported document by defining `fileName` property in [`ExcelExportProperties`](../api/grid/#excelExportProperties).

{% tab template="grid/grid",es5Template="exportfilename" %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        let excelExportProperties: ExcelExportProperties = {
            fileName:"new.xlsx"
        };
        grid.excelExport(excelExportProperties);

    }
}
grid.appendTo('#Grid');

```

{% endtab %}

## Custom data source

The excel export provides an option to define datasource dynamically before exporting. To export data dynamically, define the `dataSource` in `exportProperties`.

{% tab template="grid/grid",es5Template="exportdata"  %}

```typescript

import { Grid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        let excelExportProperties: ExcelExportProperties = {
            dataSource: data
        };
        grid.excelExport(excelExportProperties);
    }
}
grid.appendTo('#Grid');

```

{% endtab %}

## Exporting grouped records

The excel export provides outline option for grouped records which hides the detailed data for better viewing.
In grid, we have provided the outline option for the exported document when the data's are grouped.

{% tab template="grid/grid",es5Template="exportgroup" %}

```typescript

import { Grid, Toolbar, ExcelExport, Group} from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Toolbar, ExcelExport, Group);

let grid: Grid = new Grid({
    dataSource: data,
    allowExcelExport: true,
    toolbar: ['ExcelExport'],
    allowGrouping: true,
    groupSettings: { columns: ['OrderID', 'CustomerID']};
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd', textAlign: 'Right' }
    ],
    height: 230
});
grid.toolbarClick = (args: Object) => {
    if (args['item'].id === 'Grid_excelexport') {
        grid.excelExport();
    }
}
grid.appendTo('#Grid');

```

{% endtab %}

## Export the hierarchy grid

The grid has an option to export the hierarchy grid to excel document. By default, it will use `Expanded` as hierarchyExportMode. you can change the exporting option by using the `ExcelExportProperties.hierarchyExportMode` property. The available options are,

| Mode     | Behavior    |
|----------|-------------|
| Expanded | Exports the visible child grids in expanded state. |
| All      | Exports the all the child grids in expanded state. |
| None     | Exports all child grids in collapse state. |

{% tab template="grid/hierarchy-print", es5Template="hierarchyexcelexport" %}

```typescript
import { Grid, DetailRow, Toolbar, ExcelExport, ExcelExportProperties } from '@syncfusion/ej2-grids';
import { data, employeeData } from './datasource.ts';

Grid.Inject(DetailRow, Toolbar, ExcelExport);

let grid: Grid = new Grid({
    dataSource: employeeData,
    toolbar: ['ExcelExport'],
    allowExcelExport: true,
    columns: [
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'FirstName', headerText: 'First Name', width: 150 },
        { field: 'City', headerText: 'City', width: 150 },
        { field: 'Country', headerText: 'Country', width: 150 }
    ],
    childGrid: {
        dataSource: data,
        queryString: 'EmployeeID',
        columns: [
            { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
            { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
            { field: 'ShipCity', headerText: 'Ship City', width: 150 },
            { field: 'ShipName', headerText: 'Ship Name', width: 150 }
        ]
    },
    toolbarClick: toolbarClick
});
grid.appendTo('#Grid');

function toolbarClick(args) {
    if (args['item'].id === 'Grid_excelexport') {
        let exportProperties: ExcelExportProperties = {
           hierarchyExportMode: "Expanded"
        };
        grid.excelExport(exportProperties);
    }
}

```

{% endtab %}

### Limitations

* Microsoft Excel permits up to seven nested levels in outlines. So that in the grid we can able to provide only up to seven nested level
  and if it exceeds more than seven levels then the document will be exported without outline option.
  Please refer the [Microsoft Limitation](https://docs.microsoft.com/en-us/sql/reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs?view=sql-server-2017#ExcelLimitations)

## See Also

* [Exporting Grid in Cordova application](./how-to/exporting-grid-in-cordova-application)
