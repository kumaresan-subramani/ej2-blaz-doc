---
title: "Excel Exporting"
component: "Pivot Table"
description: "Export pivot table data to Excel document."
---

# Excel Export

The Excel export allows Pivot Table data to be exported as Excel document. To enable Excel export in the pivot table, set the [`allowExcelExport`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowExcelExport.html) property in [`ejs-pivotview`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) tag to **true**. Once the API is set, user needs to call the `excelExport` method for exporting on external button click.

> The pivot table component can be exported to Excel format using options available in the toolbar. For more details [`refer`](./tool-bar) here.

{% aspTab template="pivot-table/excel-export/export", sourceFiles="Export.cs" %}

{% endaspTab %}

## Multiple pivot table exporting

The Excel export provides an option to export multiple pivot table data in the same Excel file.

### Same WorkSheet

The Excel export provides support to export multiple pivot tables in same sheet. To export in same sheet, define `multipleExport.type` as `AppendToSheet` in `excelExportProperties`. It has an option to provide blank rows between pivot tables and these blank row(s) count can be defined using the`multipleExport.blankRows` property.

>By default, `multipleExport.blankRows` value is 5 between pivot table's within the same sheet.

{% aspTab template="pivot-table/excel-export/samesheet-export", sourceFiles="SameSheetExport.cs" %}

{% endaspTab %}

### New WorkSheet

Excel export provides support to export multiple pivot tables into new sheets. To export in new sheets, define  `multipleExport.type` as `NewSheet` in `excelExportProperties`.

{% aspTab template="pivot-table/excel-export/newsheet-export", sourceFiles="NewSheetExport.cs" %}

{% endaspTab %}

## Changing the pivot table style while exporting

The Excel export provides an option to change colors for headers, caption and records in pivot table before exporting. In-order to apply colors, define **theme** settings in **excelExportProperties** object and pass it as a parameter to the `excelExport` method.

>By default, material theme is applied to exported Excel document.

{% aspTab template="pivot-table/excel-export/theme-export", sourceFiles="ThemeExport.cs" %}

{% endaspTab %}

## Add header and footer while exporting

The Excel export provides an option to include header and footer content for the excel document before exporting. In-order to add header and footer, define **header** and **footer** properties in **excelExportProperties** object and pass it as a parameter to the `excelExport` method.

{% aspTab template="pivot-table/excel-export/header-footer", sourceFiles="HeaderFooter.cs" %}

{% endaspTab %}

## Changing the file name while exporting

The Excel export provides an option to change file name of the document before exporting. In-order to change the file name, define **fileName** property in **excelExportProperties** object and pass it as a parameter to the `excelExport` method.

{% aspTab template="pivot-table/excel-export/file-name", sourceFiles="FileName.cs" %}

{% endaspTab %}

## CSV Export

Also, the Excel export allows pivot table data to be exported in `CSV` file format. To export pivot table in `CSV` file format, you need to use the `csvExport` method.

{% aspTab template="pivot-table/excel-export/csv-export", sourceFiles="CSVExport.cs" %}

{% endaspTab %}

## Virtual Scroll Data

You can export the pivot table virtual scroll data as Excel/CSV document by using PivotEngine export without any performance degradation. To enable PivotEngine export in the pivot table, set the [`allowExcelExport`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowExcelExport.html) as true. You need to use the `exportToExcel` method for PivotEngine export.

> PivotEngine export will be performed while enabling virtual scrolling by default.

### Virtual Scroll Data Excel Export

{% aspTab template="pivot-table/excel-export/engine-export", sourceFiles="Export.cs" %}

{% endaspTab %}

### Virtual Scroll Data CSV Export

{% aspTab template="pivot-table/excel-export/engine-csv-export", sourceFiles="CSVExport.cs" %}

{% endaspTab %}

## Events

### ExcelQueryCellInfo

The event `excelQueryCellInfo` triggers while framing each row and value cell during Excel export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `value` - It holds the cell value.
* `column` -  It holds column information for the current cell.
* `data` - It holds the entire row data across the current cell.
* `style`  - It holds the style properties for the cell.

{% aspTab template="pivot-table/grid-customization/excel-querycell", sourceFiles="ExcelQueryCell.cs" %}

{% endaspTab %}

### ExcelHeaderQueryCellInfo

The event `excelHeaderQueryCellInfo` triggers on framing each header cell during Excel export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `cell` - It holds the current cell information.
* `style`  -  It holds the style properties for the cell.

{% aspTab template="pivot-table/grid-customization/excel-headercell", sourceFiles="ExcelHeader.cs" %}

{% endaspTab %}

## See Also

* [PDF Exporting](./pdf-export)