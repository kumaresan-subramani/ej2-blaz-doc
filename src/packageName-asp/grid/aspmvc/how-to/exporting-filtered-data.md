---
title: "Exporting Filtered Data Only"
component: "Grid"
description: "Learn how to export Filtered Data Only."
---

# Exporting Filtered Data Only

You can export the filtered data by defining the resulted data in [`dataSource`](https://ej2.syncfusion.com/documentation/api/grid/pdfExportProperties/#datasource) property of [`PdfExportProperties`](https://ej2.syncfusion.com/documentation/api/grid/pdfExportProperties/#pdfexportproperties) before export.

In the below Pdf exporting demo, We have gotten the filtered data by applying filter query to the grid data and then defines the resulted data in [`dataSource`](https://ej2.syncfusion.com/documentation/api/grid/excelExportProperties/#datasource) property and pass it to [`PdfExport`](https://ej2.syncfusion.com/documentation/api/grid/#pdfexport) method.

{% aspTab template="grid/how-to/export-filtered-data", sourceFiles="export-filtered-data.cs" %}

{% endaspTab %}
