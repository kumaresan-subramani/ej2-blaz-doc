---
title: "Toolbar"
component: "Pivot Table"
description: "Learn how to use the toolbar and customize toolbar items in the Essential JS 2 pivot table control."
---

# Toolbar

Toolbar option allows to access the frequently used features like switching between pivot table and pivot chart, changing chart types, conditional formatting, exporting, etc... with ease at runtime. This option can be enabled by setting the [`showToolbar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#showtoolbar) property in pivot table to **true**. The [`toolbar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#toolbar) property in pivot table accepts the collection of built-in toolbar options.

The following table shows built-in toolbar options and its actions.

| Built-in Toolbar Options | Actions |
|------------------------|---------|
| New | Creates a new report |
| Save | Saves the current report |
| Save As | Save as current report |
| Rename | Renames the current report |
| Delete | Deletes the current report |
| Load | Loads any report from the report list |
| Grid | Shows pivot table |
| Chart | Shows a chart in any type from the built-in list |
| Exporting | Exports the pivot table as PDF/Excel/CSV and the pivot chart as PDF and image |
| Sub-total | Shows or hides sub totals |
| Grand Total | Shows or hides grand totals |
| Conditional Formatting | Shows the conditional formatting pop-up to apply formatting |
| Number Formatting | Shows the number formatting pop-up to apply number formatting |
| Field List | Shows the fieldlist pop-up |

> The order of toolbar options can be changed by simply moving the position of items in the toolbar collection. Also if end user wants to remove any toolbar option from getting displayed, it can be simply ignored from adding into the toolbar collection.

{% tab template="pivot-table/pivot-table", es5Template="toolbar", sourceFiles="index.ts,index.html" %}

```typescript
import { pivotData } from './datasource.ts';
import {
    PivotView, FieldList, CalculatedField, Toolbar, RemoveReportArgs, NumberFormatting,
    ConditionalFormatting, IDataSet, RenameReportArgs, SaveReportArgs, FetchReportArgs, LoadReportArgs
} from '@syncfusion/ej2-pivotview';

PivotView.Inject(FieldList, CalculatedField, Toolbar, ConditionalFormatting, NumberFormatting);

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350,
    saveReport: function (args: SaveReportArgs): void {
            let reports: SaveReportArgs[] = [];
            let isSaved: boolean = false;
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reports = JSON.parse(localStorage.pivotviewReports);
            }
            if (args.report && args.reportName && args.reportName !== '') {
                reports.map(function (item: any): any {
                    if (args.reportName === item.reportName) {
                        item.report = args.report; isSaved = true;
                    }
                });
                if (!isSaved) {
                    reports.push(args);
                }
                localStorage.pivotviewReports = JSON.stringify(reports);
            }
        },
        fetchReport: function (args: FetchReportArgs): void {
            let reportCollection: string[] = [];
            let reeportList: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): void { reeportList.push(item.reportName); });
            args.reportName = reeportList;
        },
        loadReport: function (args: LoadReportArgs): void {
            let reportCollection: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): void {
                if (args.reportName === item.reportName) {
                    args.report = item.report;
                }
            });
            if (args.report) {
                pivotTableObj.dataSourceSettings = JSON.parse(args.report).dataSourceSettings;
            }
        },
        removeReport: function (args: RemoveReportArgs): void {
            let reportCollection: any[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            for (let i: number = 0; i < reportCollection.length; i++) {
                if (reportCollection[i].reportName === args.reportName) {
                    reportCollection.splice(i, 1);
                }
            }
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                localStorage.pivotviewReports = JSON.stringify(reportCollection);
            }
        },
        renameReport: function (args: RenameReportArgs): void {
            let reportCollection: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): any { if (args.reportName === item.reportName) { item.reportName = args.rename; } });
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                localStorage.pivotviewReports = JSON.stringify(reportCollection);
            }
        },
        newReport: function (): void {
            pivotTableObj.setProperties({ dataSourceSettings: { columns: [], rows: [], values: [], filters: [] } }, false);
        },
        toolbar: ['New', 'Save', 'SaveAs', 'Rename', 'Remove', 'Load',
        'Grid', 'Chart', 'Export', 'SubTotal', 'GrandTotal', 'Formatting', 'FieldList'],
        allowExcelExport: true,
        allowNumberFormatting: true,
        allowConditionalFormatting: true,
        allowPdfExport: true,
        showToolbar: true,
        allowCalculatedField: true,
        displayOption:{ view:'Both' },
        showFieldList: true,
        gridSettings: { columnWidth: 140 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Events

### FetchReport

The event [`fetchReport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#fetchreport) is triggered when dropdown list is clicked in the toolbar in-order to retrieve and populate saved reports. It has following parameter - `ReportName`. This event allows user to fetch the report names from local storage and populate the dropdown list.

### LoadReport

The event [`loadReport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#loadreport) is triggered when a report is selected from the dropdown list in the toolbar. It has following parameters - `Report` and `ReportName`. This event allows user to load the selected report to the pivot table.

### NewReport

The event [`newReport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#newreport) is triggered when the new report icon is clicked in the toolbar. It has following parameter - `Report`. This event allows user to create new report and add to the report list.

### RenameReport

The event [`renameReport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#renamereport) is triggered when rename report icon is clicked in the toolbar. It has following parameters  - `rename`, `report` and `reportName`. This event allows user to rename the selected report from the report list.

### RemoveReport

The event [`removeReport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#removereport) is triggered when remove report icon is clicked in the toolbar. It has following parameters  - `Report` and `ReportName`. This event allows user to remove the selected report from the report list.

### SaveReport

The event [`saveReport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#savereport) is triggered when save report icon is clicked in the toolbar. It has following parameters  - `Report` and `ReportName`. This event allows user to save the altered report to the report list.

### ToolbarClick

The event [`toolbarClick`](https://ej2.syncfusion.com/documentation/api/pivotview#toolbarclick) is triggered whenever toolbar item is clicked, user can modify the click function based on their requirement. It has following parameters  - `item` which holds the toolbar clicked item information.

<!-- markdownlint-disable MD028 -->

### ToolbarRender

You can customize the toolbar items in the [`toolbarRender`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#toolbarrender) event. Actions for the customized toolbar items are defined inside the customized toolbar item.

> By default, the custom toolbar items are positioned at left. You can change the position of the toolbar items by using the `align` property. In the following sample, the expand/collapse toolbar item is positioned at right.

{% tab template="pivot-table/pivot-table", es5Template="toolbar-customize", sourceFiles="index.ts,index.html" %}

```typescript
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { pivotData } from './datasource.ts';
import {
    PivotView, FieldList, CalculatedField, Toolbar, RemoveReportArgs, ToolbarArgs, NumberFormatting,
    ConditionalFormatting, IDataSet, RenameReportArgs, SaveReportArgs, FetchReportArgs, LoadReportArgs
} from '@syncfusion/ej2-pivotview';

PivotView.Inject(FieldList, CalculatedField, Toolbar, ConditionalFormatting, NumberFormatting);

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350,
    saveReport: function (args: SaveReportArgs): void {
            let reports: SaveReportArgs[] = [];
            let isSaved: boolean = false;
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reports = JSON.parse(localStorage.pivotviewReports);
            }
            if (args.report && args.reportName && args.reportName !== '') {
                reports.map(function (item: any): any {
                    if (args.reportName === item.reportName) {
                        item.report = args.report; isSaved = true;
                    }
                });
                if (!isSaved) {
                    reports.push(args);
                }
                localStorage.pivotviewReports = JSON.stringify(reports);
            }
        },
        fetchReport: function (args: FetchReportArgs): void {
            let reportCollection: string[] = [];
            let reeportList: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): void { reeportList.push(item.reportName); });
            args.reportName = reeportList;
        },
        loadReport: function (args: LoadReportArgs): void {
            let reportCollection: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): void {
                if (args.reportName === item.reportName) {
                    args.report = item.report;
                }
            });
            if (args.report) {
                pivotTableObj.dataSourceSettings = JSON.parse(args.report).dataSourceSettings;
            }
        },
        removeReport: function (args: RemoveReportArgs): void {
            let reportCollection: any[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            for (let i: number = 0; i < reportCollection.length; i++) {
                if (reportCollection[i].reportName === args.reportName) {
                    reportCollection.splice(i, 1);
                }
            }
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                localStorage.pivotviewReports = JSON.stringify(reportCollection);
            }
        },
        renameReport: function (args: RenameReportArgs): void {
            let reportCollection: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): any { if (args.reportName === item.reportName) { item.reportName = args.rename; } });
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                localStorage.pivotviewReports = JSON.stringify(reportCollection);
            }
        },
        newReport: function (): void {
            pivotTableObj.setProperties({ dataSourceSettings: { columns: [], rows: [], values: [], filters: [] } }, false);
        },
        toolbarRender: function (args: ToolbarArgs): void {
            args.customToolbar.splice(12, 0, {
                prefixIcon: 'e-tool-expand e-icons', tooltipText: 'Expand/Collapse',
                click: function (args: ClickEventArgs) {
                    pivotTableObj.dataSourceSettings.expandAll = !pivotTableObj.dataSourceSettings.expandAll;
                },
                align: 'Right'
            });
        },
        toolbar: ['New', 'Save', 'SaveAs', 'Rename', 'Remove', 'Load',
        'Grid', 'Chart', 'Export', 'SubTotal', 'GrandTotal', 'Formatting', 'FieldList'],
        allowExcelExport: true,
        allowNumberFormatting: true,
        allowConditionalFormatting: true,
        allowPdfExport: true,
        showToolbar: true,
        allowCalculatedField: true,
        displayOption:{ view:'Both' },
        showFieldList: true,
        gridSettings: { columnWidth: 140 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### BeforeExport

The pivot table (or) pivot chart can be exported as a pdf, excel, csv etc.,  document using the toolbar options. And, you can customize the export settings for exporting document by using the [`beforeExport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#beforeexport) event in the toolbar.

For example, you can add the header and footer for the pdf document by setting the `header` and `footer` properties for the `pdfExportProperties` in the [`beforeExport`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#beforeexport) event.

{% tab template="pivot-table/pivot-table", es5Template="toolbar", sourceFiles="index.ts,index.html" %}

```typescript
import { pivotData } from './datasource.ts';
import {
    PivotView, FieldList, CalculatedField, Toolbar, RemoveReportArgs,
    ConditionalFormatting, IDataSet, RenameReportArgs, SaveReportArgs, FetchReportArgs, LoadReportArgs
} from '@syncfusion/ej2-pivotview';

PivotView.Inject(FieldList, CalculatedField, Toolbar, ConditionalFormatting);

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350,
    saveReport: function (args: SaveReportArgs): void {
            let reports: SaveReportArgs[] = [];
            let isSaved: boolean = false;
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reports = JSON.parse(localStorage.pivotviewReports);
            }
            if (args.report && args.reportName && args.reportName !== '') {
                reports.map(function (item: any): any {
                    if (args.reportName === item.reportName) {
                        item.report = args.report; isSaved = true;
                    }
                });
                if (!isSaved) {
                    reports.push(args);
                }
                localStorage.pivotviewReports = JSON.stringify(reports);
            }
        },
        fetchReport: function (args: FetchReportArgs): void {
            let reportCollection: string[] = [];
            let reeportList: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): void { reeportList.push(item.reportName); });
            args.reportName = reeportList;
        },
        loadReport: function (args: LoadReportArgs): void {
            let reportCollection: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): void {
                if (args.reportName === item.reportName) {
                    args.report = item.report;
                }
            });
            if (args.report) {
                pivotTableObj.dataSourceSettings = JSON.parse(args.report).dataSourceSettings;
            }
        },
        removeReport: function (args: RemoveReportArgs): void {
            let reportCollection: any[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            for (let i: number = 0; i < reportCollection.length; i++) {
                if (reportCollection[i].reportName === args.reportName) {
                    reportCollection.splice(i, 1);
                }
            }
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                localStorage.pivotviewReports = JSON.stringify(reportCollection);
            }
        },
        renameReport: function (args: RenameReportArgs): void {
            let reportCollection: string[] = [];
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                reportCollection = JSON.parse(localStorage.pivotviewReports);
            }
            reportCollection.map(function (item: any): any { if (args.reportName === item.reportName) { item.reportName = args.rename; } });
            if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
                localStorage.pivotviewReports = JSON.stringify(reportCollection);
            }
        },
        newReport: function (): void {
            pivotTableObj.setProperties({ dataSourceSettings: { columns: [], rows: [], values: [], filters: [] } }, false);
        },
        beforeExport: function(args: BeforeExportEventArgs): void {
            args.excelExportProperties = {
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
            args.pdfExportProperties = {
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
        },
        toolbar: ['New', 'Save', 'SaveAs', 'Rename', 'Remove', 'Load',
        'Grid', 'Chart', 'Export', 'SubTotal', 'GrandTotal', 'ConditionalFormatting', 'FieldList'],
        allowExcelExport: true,
        allowConditionalFormatting: true,
        allowPdfExport: true,
        showToolbar: true,
        allowCalculatedField: true,
        displayOption:{ view:'Both' },
        showFieldList: true,
        gridSettings: { columnWidth: 140 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## See Also

* [Toolbar Component](../../toolbar/getting-started.html)
* [Excel Exporting](./excel-export)
* [PDF Exporting](./pdf-export)
