---
title: "PDF Exporting"
component: "Pivot Table"
description: "Export pivot table data to PDF document."
---

# PDF Export

PDF export allows exporting pivot table data as PDF document. To enable PDF export in the pivot table, set the `allowPdfExport` as true. You need to use the `pdfExport` method for PDF exporting.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.pdfExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Multiple pivot table exporting

PDF export provides an option for exporting multiple pivot tables to same file. In this exported document, each pivot table will be exported to new page of document in same file.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  public dataSourceSettings1: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: true,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj1: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj1 = d!} id='PivotView1' height={280} dataSourceSettings={this.dataSourceSettings1} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let firstGridPdfExport: Promise<Object> = this.pivotObj.grid.pdfExport({}, true);
    firstGridPdfExport.then((pdfData: Object) => {
        this.pivotObj1.pdfExport({}, false, pdfData);
    });
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Customization during PDF export

PDF export provides option to customize mapping of pivot table to the exported PDF document.

### To add header and footer

You can customize text, page number, line, page size and changing orientation in header and footer.

#### How to write a text in header/footer

You can add text either in header or footer of the exported PDF document like in the below code example.

{% tab compileJsx=true%}

```typescript

let pdfExportProperties: PdfExportProperties = {
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

{% endtab %}

#### How to draw a line in header/footer

You can add line either in header or footer of the exported PDF document like in the below code example.

Supported line styles:
* dash
* dot
* dashdot
* dashdotdot
* solid

{% tab compileJsx=true%}

```typescript

let pdfExportProperties: PdfExportProperties = {
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

{% endtab %}

#### Add page number in header/footer

You can add page number either in header or footer of exported PDF document like in the below code example.

Supported page number types:
* LowerLatin - a, b, c,
* UpperLatin - A, B, C,
* LowerRoman - i, ii, iii,
* UpperRoman - I, II, III,
* Number - 1,2,3.

{% tab compileJsx=true%}

```typescript

 let pdfExportProperties: PdfExportProperties = {
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

{% endtab %}

The below code illustrates the PDF export customization options.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { PdfExportProperties } from '@syncfusion/ej2-grids';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let pdfExportProperties: PdfExportProperties = {
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
    this.pivotObj.pdfExport(pdfExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Changing the file name while exporting

The PDF export provides an option to change file name of the document before exporting. In-order to change the file name, define **fileName** property in **pdfExportProperties** object and pass it as a parameter to the [`pdfExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#pdfexport) method.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { PdfExportProperties } from '@syncfusion/ej2-grids';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let pdfExportProperties: PdfExportProperties = {
      fileName: 'sample.pdf'
    };
    this.pivotObj.pdfExport(pdfExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Changing page orientation while exporting

The PDF export provides an option to change page orientation of the document before exporting. In-order to change the page orientation, define **pageOrientation** property in **pdfExportProperties** object and pass it as a parameter to the [`pdfExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#pdfexport) method. By default, the page orientation will be in **Portrait** and it can be changed to **Landscape** based on user requirement.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { PdfExportProperties } from '@syncfusion/ej2-grids';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let pdfExportProperties: PdfExportProperties = {
      pageOrientation: 'Landscape'
    };
    this.pivotObj.pdfExport(pdfExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Changing page size while exporting

The PDF export provides an option to change page size of the document before exporting. In-order to change the page size, define **pageSize** property in **pdfExportProperties** object and pass it as a parameter to the [`pdfExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#pdfexport) method.

**Supported page sizes are:** Letter, Note, Legal, A0, A1, A2, A3, A5, A6, A7, A8, A9, B0, B1, B2, B3, B4, B5, Archa, Archb, Archc, Archd, Arche, Flsa, HalfLetter, Letter11x17, Ledger.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { PdfExportProperties } from '@syncfusion/ej2-grids';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let pdfExportProperties: PdfExportProperties = {
      pageSize: 'Letter'
    };
    this.pivotObj.pdfExport(pdfExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Changing the pivot table style while exporting

The PDF export provides an option to change colors for headers, caption and records in pivot table before exporting. In-order to apply colors, define **theme** settings in **pdfExportProperties** object and pass it as a parameter to the [`pdfExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#pdfexport) method.

> By default, material theme will be applied to the pivot table during PDF exporting.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { PdfExportProperties } from '@syncfusion/ej2-grids';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let pdfExportProperties: PdfExportProperties = {
      theme: {
          header: {
              fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true, borders: { color: '#64FA50', lineStyle: 'Thin' }
          },
          record: {
              fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true
          },
          caption: {
              fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true
          }
      }
    };
    this.pivotObj.pdfExport(pdfExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

<!-- markdownlint-disable MD009 -->

### Changing default font while exporting

By default, the pivot table uses "Helvetica" font in the exported document. But it can be changed using the [`theme`](https://ej2.syncfusion.com/react/documentation/api/grid/pdfExportProperties/#theme) property in [`pdfExportProperties`](https://ej2.syncfusion.com/react/documentation/api/grid/pdfExportProperties/).

The available built-in fonts are, 

* Helvetica 
* TimesRoman 
* Courier 
* Symbol 
* ZapfDingbats 

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { PdfStandardFont, PdfFontFamily, PdfFontStyle } from '@syncfusion/ej2-pdf-export';

    ...

    let pdfExportProperties: PdfExportProperties = {
               theme: { 
                header: {font:  new PdfStandardFont(PdfFontFamily.TimesRoman, 11, PdfFontStyle.Bold) }, 
                caption: { font: new PdfStandardFont(PdfFontFamily.TimesRoman, 9) }, 
                record: { font: new PdfStandardFont(PdfFontFamily.TimesRoman, 10) } 
                } 
            };

```

### Adding custom font while exporting

In addition to existing built-in fonts, custom fonts can also be used. The custom font should be in **Base64** format and mention it in **PdfTrueTypeFont** class. In the following example, we have used **Advent Pro** font family that supports **Hungarian** language.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData, base64AlgeriaFont } from './datasource';
import { PdfExportProperties } from '@syncfusion/ej2-grids';
import { PdfTrueTypeFont } from '@syncfusion/ej2-pdf-export';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let pdfExportProperties: PdfExportProperties = {
               theme: { 
                header: {font:  new PdfTrueTypeFont(base64AlgeriaFont, 11) }, 
                caption: { font: new PdfTrueTypeFont(base64AlgeriaFont, 9) }, 
                record: { font: new PdfTrueTypeFont(base64AlgeriaFont, 10) } 
                } 
            };
    this.pivotObj.pdfExport(pdfExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Virtual Scroll Data

You can export the pivot table virtual scroll data as PDF document by using PivotEngine export without any performance degradation. To enable PivotEngine export in the pivot table, set the `allowPdfExport` as true. You need to use the `exportToPDF` method for PivotEngine export.

> To use PivotEngine export, You need to inject the `PDFExport` module in pivot table.
> PivotEngine export will be performed while enabling virtual scrolling by default

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, Inject, PDFExport } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}><Inject services={[PDFExport]} /></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.pdfExportModule.exportToPDF();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Repeat row headers

Repeat row headers on each page can be achieved using PivotEngine export option. To disable repeat row headers, you need to set `allowRepeatHeader` to **false** in beforeExport event. You need to use the `exportToPDF` method for PivotEngine export.

> To use PivotEngine export, You need to inject the `PDFExport` module in pivot table.
> By default, repeat row headers is enabled in the PivotEngine export.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, Inject, PDFExport } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={280} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}><Inject services={[PDFExport]} /></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.pdfExportModule.exportToPDF();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### PdfQueryCellInfo

The event `pdfQueryCellInfo` triggers on framing each row and value cell during PDF export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `value` - It holds the cell value.
* `column` -  It holds column information for the current cell.
* `data` - It holds the entire row data across the current cell.
* `style` - It holds the style properties for the cell.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    columnWidth: 140,
    pdfQueryCellInfo: this.pdfQueryCellInfo.bind(this)
  } as GridSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  pdfQueryCellInfo(args: PdfQueryCellInfoEventArgs): void {
    //triggers every time for header cell while rendering
  }
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }
   btnClick(): void {
    this.pivotObj.pdfExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

### PdfHeaderQueryCellInfo

The event `pdfHeaderQueryCellInfo` triggers on framing each column header cell during PDF export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `cell` - It holds the current rendering cell information.
* `style` - It holds the style properties for the cell.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { GridSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/gridsettings';

class App extends React.Component<{}, {}>{
  public gridSettings: GridSettings = {
    columnWidth: 140,
    pdfHeaderQueryCellInfo: this.pdfHeaderQueryCellInfo.bind(this)
  } as GridSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  pdfHeaderQueryCellInfo(args: PdfHeaderQueryCellInfoEventArgs): void {
    //triggers every time for header cell while rendering
  }
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }
   btnClick(): void {
    this.pivotObj.pdfExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## See Also

* [Excel Exporting](./excel-export)