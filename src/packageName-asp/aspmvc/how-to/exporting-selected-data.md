---
title: "Exporting Selected Data"
component: "Grid"
description: "Learn how to Export Selected data only."
---

# Exporting the Selected Records

You can export the selected records data by passing it to [`dataSource`](https://ej2.syncfusion.com/documentation/api/grid/pdfExportProperties/#datasource) of [`PdfExportProperties`](https://ej2.syncfusion.com/documentation/api/grid/pdfExportProperties/#pdfexportproperties) in the [`ToolbarClick`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ToolbarClick.html) event.

In the below exporting demo, We can get the selected records using **getSelectedRecords** method and pass the selected data to **PdfExport** or **excelExport** property.

{% aspTab template="grid/how-to/export-selected-data", sourceFiles="selected-data.cs" %}

{% endaspTab %}