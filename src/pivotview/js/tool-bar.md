---
title: "Toolbar"
component: "Pivot Table"
description: "Learn how to use the toolbar and customize toolbar items in the Essential JS 2 pivot table control."
---

# Toolbar

Toolbar option allows to access the frequently used features like switching between pivot table and pivot chart, changing chart types, conditional formatting, exporting, etc... with ease at runtime. This option can be enabled by setting the [`showToolbar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#showtoolbar) property in pivot table to **true**. The [`toolbar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#toolbar) property in pivot table accepts the collection of built-in toolbar options.

## Built-in Toolbar Options

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
| Chart | Shows a chart in any type from the built-in list and option to enable/disable multiple axes |
| Exporting | Exports the pivot table as PDF/Excel/CSV and the pivot chart as PDF and image |
| Sub-total | Shows or hides sub totals |
| Grand Total | Shows or hides grand totals |
| Conditional Formatting | Shows the conditional formatting pop-up to apply formatting |
| Number Formatting | Shows the number formatting pop-up to apply number formatting |
| Field List | Shows the fieldlist pop-up |
| MDX | Shows the MDX query that was run to retrieve data from the OLAP data source. **NOTE: This applies only to the OLAP data source.** |

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

## Show desired chart types in the dropdown menu

By default, all chart types are displayed in the dropdown menu included in the toolbar. However, based on the request for an application, we may need to show selective chart types on our own. This can be achieved using the [`chartTypes`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/#charttypes) property. To know more about supporting chart types, [`click here`](https://ej2.syncfusion.com/javascript/documentation/pivotview/pivot-chart/#chart-types).

{% tab template="pivot-table/pivot-table", es5Template="toolbar-charttypes", sourceFiles="index.ts,index.html" %}

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
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
    },
        height: 350,
        toolbar: ['Grid','Chart'],
        chartTypes:['Column','Bar','Line','Area'],
        showToolbar: true,
        displayOption:{ view:'Both' },
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Switch the chart to multiple axes

In the chart, the user can switch from single axis to multiple axes with the help of the built-in checkbox available inside the chart type dropdown menu in the toolbar. For more information [`refer here`](https://ej2.syncfusion.com/javascript/documentation/pivotview/pivot-chart/#multi-axis).

![output](images/chart-option.png)

<!-- markdownlint-disable MD009 -->

## Show or hide legend

In the chart, legend can be shown or hidden dynamically with the help of the built-in option available in the chart type drop-down menu.
> By default, the legend is not be visible for the accumulation chart types like pie, doughnut, pyramid, and funnel. Users can enable or disable using the built-in checkbox option.

![output](images/chart-legend.png)

## Adding custom option to the toolbar

In addition to the existing built-in toolbar items, new toolbar item(s) may also be included. This can be achieved by using the [`toolbarRender`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#toolbarrender) event. The action of the new toolbar item(s) can also be defined within this event. 

> The new toolbar item(s) can be added to the desired position in the toolbar using the `splice` option.

{% tab template="pivot-table/pivot-table", es5Template="toolbar-customize", sourceFiles="index.ts,index.html" %}

```typescript
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { pivotData } from './datasource.ts';
import {
    PivotView, Toolbar, ToolbarArgs, IDataSet
} from '@syncfusion/ej2-pivotview';

PivotView.Inject(Toolbar);

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        enableSorting: true,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350,
    toolbarRender: function (args: ToolbarArgs): void {
        args.customToolbar.splice(12, 0, {
                prefixIcon: 'e-tool-expand e-icons', tooltipText: 'Expand/Collapse',
                click: this.toolbarClicked.bind(this)
        });
    },
    toolbarClicked: function(args: any): void {
        pivotTableObj.dataSourceSettings.expandAll = !pivotTableObj.dataSourceSettings.expandAll;
    },
    toolbar: ['Expand/Collapse'],
    showToolbar: true,
    displayOption:{ view:'Both' },
    gridSettings: { columnWidth: 140 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

<!-- markdownlint-disable MD009 -->

## Save and load report as a JSON file 

The current pivot report can be saved as a JSON file in the desired path and loaded back to the pivot table at any time.

{% tab template="pivot-table/json-file", es5Template="json-file", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
    },
    showGroupingBar: true,
    height: 350,
    dataBound: function(args: ny): void {
            var dataSource = JSON.parse(pivotTableObj.getPersistData()).dataSourceSettings.dataSource;
            var a = document.getElementById('save');
            var mime_type = 'application/octet-stream'; // text/html, image/png, et c
            a.setAttribute('download', 'pivot.JSON');
            a.href = 'data:'+ mime_type +';base64,'+ btoa(JSON.stringify(dataSource) || '');
            document.getElementById('files').addEventListener('change', this.readBlob, false);
        },
        readBlob: function (): void {
        var files = document.getElementById('load').files;
        var file = files[0];
        var start = 0;
        var stop = file.size - 1;
        var reader = new FileReader();
        reader.onloadend = function(evt) {
            if (evt.target.readyState == FileReader.DONE) {
                pivotTableObj.dataSource = JSON.parse(evt.target.result);
            }
        };
        var blob = file.slice(start, stop + 1);
        reader.readAsBinaryString(blob);
        }
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

### ToolbarRender 

The [`toolbarRender`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#toolbarrender) event is triggered when the toolbar is rendered. It has the `customToolbar` parameter. This event helps to customize the built-in toolbar items and to [`include new toolbar item(s)`](https://ej2.syncfusion.com/javascript/documentation/pivotview/tool-bar/#adding-custom-option-to-the-toolbar).

{% tab template="pivot-table/pivot-table", es5Template="toolbar-customize-inbuilt", sourceFiles="index.ts,index.html" %}

```typescript
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { pivotData } from './datasource.ts';
import {
    PivotView, Toolbar, ToolbarArgs, IDataSet, SaveReportArgs, FieldList
} from '@syncfusion/ej2-pivotview';

PivotView.Inject(Toolbar, FieldList);

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
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
    toolbarRender: function (args: ToolbarArgs): void {
         args.customToolbar.splice(2, 0, {
                prefixIcon: 'e-pivot-format-toolbar e-icons', tooltipText: 'Custom Button',
                click: this.customButton.bind(this),
        });
        args.customToolbar.splice(3, 0, {
                prefixIcon: 'e-tool-expand e-icons', tooltipText: 'Expand/Collapse',
                click: this.toolbarClicked.bind(this),
        });
        args.customToolbar[0].align = "Left";
        args.customToolbar[1].align = "Center";
        args.customToolbar[2].align = "Right";
    },
    customButton: function(args: any): void {
        // Here you can customize the click event for custom button
    },
    toolbarClicked: function(args: any): void {
        pivotTableObj.dataSourceSettings.expandAll = !pivotTableObj.dataSourceSettings.expandAll;
    },
    toolbar: ['Save', 'Export', 'FieldList'],
    showToolbar: true,
    showFieldList: true,
    displayOption:{ view:'Both' },
    gridSettings: { columnWidth: 140 }
});
pivotTableObj.appendTo('#PivotTable');

```

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