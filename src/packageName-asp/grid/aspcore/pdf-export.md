---
title: "PDF Export"
component: "Grid"
description: "Documentation on exporting DataGrid content to PDF format and customizing the exported document with multi-export, headers and footers, and file name changes."
---

# PDF Export

PDF export allows exporting Grid data to PDF document. You need to use the
 **PdfExport** method for exporting. To enable PDF export in the grid, set the [`allowPdfExport`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowPdfExport.html) as true.

{% aspTab template="grid/pdf-export/pdf-export", sourceFiles="pdf-export.cs" %}

{% endaspTab %}

## Multiple exporting

PDF export provides an option for exporting multiple grids to same file. In this exported document, each grid will be exported to new page of document in same file.

{% aspTab template="grid/pdf-export/multiple", sourceFiles="multiple.cs" %}

{% endaspTab %}

## To customize PDF export

PDF export provides an option to customize mapping of grid to exported PDF document.

### File Name for Exported document

You can assign the file name for the exported document by defining **fileName** property in **PdfExportProperties**.

{% aspTab template="grid/pdf-export/export-filename", sourceFiles="export-filename.cs" %}

{% endaspTab %}

### Default Fonts for PDF exporting

By default, grid uses **Helvetica** font in the exported document. You can change the default font by using **pdfExportProperties.theme** property. The available default fonts are,

* Helvetica
* TimesRoman
* Courier
* Symbol
* ZapfDingbats

The code example for changing default font,

```typescript

    let pdfExportProperties = {
        theme: {
            header: {font:  new ej.pdfexport.PdfStandardFont(ej.pdfexport.PdfFontFamily.TimesRoman, 11, PdfFontStyle.Bold),
            caption: { font: new ej.pdfexport.PdfStandardFont(ej.pdfexport.PdfFontFamily.TimesRoman, 9) },
            record: { font: new ej.pdfexport.PdfStandardFont(ej.pdfexport.PdfFontFamily.TimesRoman, 10) }
        }
    };

```

### Add Custom Font for PDF exporting

You can change the default font of Grid header, content and caption cells in the exported document by using **pdfExportProperties.theme** property.

In the following example, we have used Advent Pro font to export the grid with Hungarian fonts.

{% aspTab template="grid/pdf-export/customfont", sourceFiles="customfont.cs" %}

{% endaspTab %}

> **ej.pdfexport.PdfTrueTypeFont** accepts base 64 format of the Custom Font.

### To add header and footer

You can customize text, page number, line, page size and changing orientation in header and footer.

#### How to write a text in header/footer

You can add text either in Header or Footer of exported PDF document.

```typescript

var exportProperties = {
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

```

#### How to draw a line in header/footer

you can add line either in Header or Footer of the exported PDF document.

Supported line styles:
* dash
* dot
* dashdot
* dashdotdot
* solid

```typescript

var exportProperties = {
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

you can add page number either in Header or Footer of exported PDF document.

Supported page number types:
* LowerLatin - a, b, c,
* UpperLatin - A, B, C,
* LowerRoman - i, ii, iii,
* UpperRoman - I, II, III,
* Number - 1,2,3.

```typescript

 var exportProperties = {
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

#### Insert an image in header/footer

Image (Base64 string) can be added in the exported document in header/footer using the **exportProperties**.

```typescript

var exportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'Image',
                src: image,
                position: { x: 40, y: 10 },
                size: { height: 100, width: 250 },
            }
        ]
    }
}

```

The below code illustrates the pdf export customization.

{% aspTab template="grid/pdf-export/header-footer", sourceFiles="header-footer.cs" %}

{% endaspTab %}

### How to change page orientation

Page orientation can be changed Landscape(Default Portrait) for the exported document using the **exportProperties**.

{% aspTab template="grid/pdf-export/orientation", sourceFiles="orientation.cs" %}

{% endaspTab %}

### How to change page size

Page size can be customized for the exported document using the **exportProperties**.
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

{% aspTab template="grid/pdf-export/page-size", sourceFiles="page-size.cs" %}

{% endaspTab %}

### Export current page

PDF export provides an option to export the current page into PDF. To export current page, define the **exportType** to **currentpage**.

{% aspTab template="grid/pdf-export/export-current", sourceFiles="export-current.cs" %}

{% endaspTab %}

### Export hidden columns

PDF export provides an option to export hidden columns of Grid by defining the **includeHiddenColumn** as **true**.

{% aspTab template="grid/pdf-export/export-hidden", sourceFiles="export-hidden.cs" %}

{% endaspTab %}

### Show or Hide columns on Exported PDF

You can show a hidden column or hide a visible column while exporting the grid using [`toolbarClick`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ToolbarClick.html) and [`pdfExportComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PdfExportComplete.html) event.

In the [`toolbarClick`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ToolbarClick.html) event, based on **args.item.id** as **Grid_pdfexport**. We can show or hide columns by setting [`visible`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Visible.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) to **true** or **false** respectively.

In the [`pdfExportComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PdfExportComplete.html) event, We have reversed the state back to the previous state.

In the below example, we have **CustomerID** as a hidden column in the grid. While exporting, we have changed **CustomerID** to visible column and **ShipCity** as hidden column.

{% aspTab template="grid/pdf-export/show-hide", sourceFiles="show-hide.cs" %}

{% endaspTab %}

### Conditional Cell Formatting

Grid cells in the exported PDF can be customized or formatted using [`pdfQueryCellInfo`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PdfQueryCellInfo.html) event. In this event, we can format the grid cells of exported PDF document based on the column cell value.

In the below sample, we have set the **background** color for **Freight** column in the exported document by **args.cell** and **backgroundColor** property.

{% aspTab template="grid/pdf-export/cell-format", sourceFiles="pdf-export.cs" %}

{% endaspTab %}

### Theme

PDF export provides an option to include theme for exported PDF document.

To apply theme in exported PDF, define the **theme** in **exportProperties**.

{% aspTab template="grid/pdf-export/theme", sourceFiles="theme.cs" %}

{% endaspTab %}

> By default, material theme is applied to exported PDF document.

## Custom data source

PDF export provides an option to define datasource dynamically before exporting. To export data dynamically, define the **dataSource** in **exportProperties**.

{% aspTab template="grid/pdf-export/custom-data", sourceFiles="custom-data.cs" %}

{% endaspTab %}

## Export the hierarchy grid

The grid have an option to export the hierarchy grid to pdf document. By default, grid will exports the master grid with expanded child grids alone. you can change the exporting option by using the **PdfExportProperties.hierarchyExportMode** property. The available options are,

| Mode     | Behavior    |
|----------|-------------|
| Expanded | Exports the master grid with expanded child grids. |
| All      | Exports the master grid with all the child grids. |
| None     | Exports the master grid alone. |

{% aspTab template="grid/pdf-export/hierarchy", sourceFiles="hierarchy.cs" %}

{% endaspTab %}

## Repeat column header on every page

By default, column header will be placed on the first page of the pdf document but you can display column header on every page using **repeatHeader** property of **pdfGrid**.

In the below sample, we have enabled **repeatHeader** property in [`pdfHeaderQueryCellInfo`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PdfHeaderQueryCellInfo.html) event to show the header on every page.

{% aspTab template="grid/pdf-export/repeat-header", sourceFiles="repeat-header" %}

{% endaspTab %}
