---
title: "PDF Exporting"
component: "Pivot Table"
description: "Export pivot table data to PDF document."
---

# PDF Export

PDF export allows exporting pivot table data as PDF document. To enable PDF export in the pivot table, set the [`allowPdfExport`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowPdfExport.html) as true. You need to use the `pdfExport` method for PDF exporting.

{% aspTab template="pivot-table/pdf-export/export", sourceFiles="Export.cs" %}

{% endaspTab %}

## Multiple pivot table exporting

PDF export provides an option for exporting multiple pivot tables to same file. In this exported document, each pivot table will be exported to new page of document in same file.

{% aspTab template="pivot-table/pdf-export/multiple-export", sourceFiles="MultipleExport.cs" %}

{% endaspTab %}

## Customization during PDF export

PDF export provides option to customize mapping of pivot table to the exported PDF document.

### To add header and footer

You can customize text, page number, line, page size and changing orientation in header and footer.

#### How to write a text in header/footer

You can add text either in header or footer of the exported PDF document like in the below code example.

```javascript

var pdfExportProperties = {
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

```javascript

var pdfExportProperties = {
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

```javascript

 var pdfExportProperties = {
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

{% aspTab template="pivot-table/pdf-export/header-footer", sourceFiles="HeaderFooter.cs" %}

{% endaspTab %}

### Changing the file name while exporting

The PDF export provides an option to change file name of the document before exporting. In-order to change the file name, define **fileName** property in **pdfExportProperties** object and pass it as a parameter to the `pdfExport` method.

{% aspTab template="pivot-table/pdf-export/file-name", sourceFiles="FileName.cs" %}

{% endaspTab %}

### Changing page orientation while exporting

The PDF export provides an option to change page orientation of the document before exporting. In-order to change the page orientation, define **pageOrientation** property in **pdfExportProperties** object and pass it as a parameter to the `pdfExport` method. By default, the page orientation will be in **Portrait** and it can be changed to **Landscape** based on user requirement.

{% aspTab template="pivot-table/pdf-export/page-layout", sourceFiles="PageLayout.cs" %}

{% endaspTab %}

### Changing page size while exporting

The PDF export provides an option to change page size of the document before exporting. In-order to change the page size, define **pageSize** property in **pdfExportProperties** object and pass it as a parameter to the `pdfExport` method.

**Supported page sizes are:** Letter, Note, Legal, A0, A1, A2, A3, A5, A6, A7, A8, A9, B0, B1, B2, B3, B4, B5, Archa, Archb, Archc, Archd,
Arche, Flsa, HalfLetter, Letter11x17, Ledger.

{% aspTab template="pivot-table/pdf-export/page-size", sourceFiles="PageSize.cs" %}

{% endaspTab %}

## Changing the pivot table style while exporting

The PDF export provides an option to change colors for headers, caption and records in pivot table before exporting. In-order to apply colors, define **theme** settings in **pdfExportProperties** object and pass it as a parameter to the `pdfExport` method.

> By default, material theme is applied to exported PDF document.

{% aspTab template="pivot-table/pdf-export/theme-export", sourceFiles="ThemeExport.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD009 -->

### Changing default font while exporting

By default, the pivot table uses "Helvetica" font in the exported document. But it can be changed using the **theme** property in **pdfExportProperties**.

The available built-in fonts are, 

* Helvetica 
* TimesRoman 
* Courier 
* Symbol 
* ZapfDingbats 

```javascript

var pdfExportProperties = {
    theme: { 
                header: {font:  new PdfStandardFont(PdfFontFamily.TimesRoman, 11, PdfFontStyle.Bold) }, 
                caption: { font: new PdfStandardFont(PdfFontFamily.TimesRoman, 9) }, 
                record: { font: new PdfStandardFont(PdfFontFamily.TimesRoman, 10) } 
            } 
}

```

### Adding custom font while exporting

In addition to existing built-in fonts, custom fonts can also be used. The custom font should be in **Base64** format and mention it in **PdfTrueTypeFont** class. In the following example, we have used **Advent Pro** font family that supports **Hungarian** language.

{% aspTab template="pivot-table/pdf-export/non-english-export",  sourceFiles="non-english-export.cs" %}

{% endaspTab %}

> The non-English alphabets can also be exported properly by setting its appropriate font.

## Virtual Scroll Data

You can export the pivot table virtual scroll data as PDF document by using PivotEngine export without any performance degradation. To enable PivotEngine export in the pivot table, set the `allowPdfExport` as true. You need to use the `exportToPDF` method for PivotEngine export.

> PivotEngine export will be performed while enabling virtual scrolling by default

{% aspTab template="pivot-table/pdf-export/engine-export", sourceFiles="Export.cs" %}

{% endaspTab %}

### Repeat row headers

Repeat row headers on each page can be achieved using PivotEngine export option. To disable repeat row headers, you need to set `allowRepeatHeader` to **false** in beforeExport event. You need to use the `exportToPDF` method for PivotEngine export.

> By default, repeat row headers is enabled in the PivotEngine export.

{% aspTab template="pivot-table/pdf-export/repeat-headers", sourceFiles="Export.cs" %}

{% endaspTab %}

## Events

### PdfQueryCellInfo

The event `pdfQueryCellInfo` triggers on framing each row and value cell during PDF export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `value` - It holds the cell value.
* `column` -  It holds column information for the current cell.
* `data` - It holds the entire row data across the current cell.
* `style` - It holds the style properties for the cell.

{% aspTab template="pivot-table/grid-customization/pdf-querycell", sourceFiles="PdfQueryCell.cs" %}

{% endaspTab %}

### PdfHeaderQueryCellInfo

The event `pdfHeaderQueryCellInfo` triggers on framing each column header cell during PDF export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `cell` - It holds the current rendering cell information.
* `style` - It holds the style properties for the cell.

{% aspTab template="pivot-table/grid-customization/pdf-headercell", sourceFiles="PdfHeader.cs" %}

{% endaspTab %}

## See Also

* [Excel Exporting](./excel-export)