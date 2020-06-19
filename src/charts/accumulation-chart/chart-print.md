---
title: " Accumulation Chart Print and Export | ASP.NET Core Blazor "

component: "Accumulation Chart"

description: "Accumultion chart have a public methods for print or export the rendered chart"
---

# Print and Export

## Print

The rendered chart can be printed directly from the browser by calling the public method print.

{% aspTab template="chart/accumulation-charts/chart-print/print", sourceFiles="print.razor" %}

{% endaspTab %}

## Export

The rendered chart can be exported to `Image`(jpeg or png) or `SVG` or `PDF` format by using the export method. Input parameters for this method are `Export` Type for `format` and `FileName` of result.

{% aspTab template="chart/accumulation-charts/chart-print/export", sourceFiles="export.razor" %}

{% endaspTab %}