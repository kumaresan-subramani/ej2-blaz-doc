---
title: "Excel Exporting"
component: "Pivot Table"
description: "Export pivot table data to Excel document."
---

# Excel Export

The Excel export allows Pivot Table data to be exported as Excel document. To enable Excel export in the pivot table, set the [`allowExcelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowexcelexport) property in [`PivotView`](https://ej2.syncfusion.com/react/documentation/api/pivotview) to **true**. Once the API is set, user needs to call the [`excelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#excelexport) method for exporting on external button click.

> The pivot table component can be exported to Excel format using options available in the toolbar. For more details [`refer`](./tool-bar) here.

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.excelExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Multiple pivot table exporting

The Excel export provides an option to export multiple pivot table data in the same Excel file.

### Same WorkSheet

The Excel export provides support to export multiple pivot tables in same sheet. To export in same sheet, define `multipleExport.type` as `AppendToSheet` in `excelExportProperties`. It has an option to provide blank rows between pivot tables and these blank row(s) count can be defined using the`multipleExport.blankRows` property.

>By default, `multipleExport.blankRows` value is 5 between pivot tables within the same sheet.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj1 = d!} id='PivotView1' height={350} dataSourceSettings={this.dataSourceSettings1} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let excelExportProperties: ExcelExportProperties = {
        multipleExport: { type: 'AppendToSheet', blankRows: 2 }
    };
    let firstGridExport: Promise<any> = this.pivotObj.grid.excelExport(excelExportProperties, true);
    firstGridExport.then((fData: any) => {
      this.pivotObj1.excelExport(excelExportProperties, false, fData);
    });
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### New WorkSheet

Excel export provides support to export multiple pivot tables into new sheets. To export in new sheets, define  `multipleExport.type` as `NewSheet` in `excelExportProperties`.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj1 = d!} id='PivotView1' height={350} dataSourceSettings={this.dataSourceSettings1} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let excelExportProperties: ExcelExportProperties = {
        multipleExport: { type: 'NewSheet' }
    };
    let firstGridExport: Promise<any> = this.pivotObj.grid.excelExport(excelExportProperties, true);
    firstGridExport.then((fData: any) => {
      this.pivotObj1.excelExport(excelExportProperties, false, fData);
    });
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Changing the pivot table style while exporting

The Excel export provides an option to change colors for headers, caption and records in pivot table before exporting. In-order to apply colors, define **theme** settings in **excelExportProperties** object and pass it as a parameter to the [`excelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#excelexport) method.

> By default, material theme will be applied to the pivot table during Excel exporting.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let excelExportProperties: ExcelExportProperties = {
      theme:
      {
          header: { fontName: 'Segoe UI', fontColor: '#666666' },
          record: { fontName: 'Segoe UI', fontColor: '#666666' },
          caption: { fontName: 'Segoe UI', fontColor: '#666666' }
      }
    };
    this.pivotObj.grid.excelExport(excelExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Add header and footer while exporting

The Excel export provides an option to include header and footer content for the excel document before exporting. In-order to add header and footer, define **header** and **footer** properties in **excelExportProperties** object and pass it as a parameter to the [`excelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#excelexport) method.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let excelExportProperties: ExcelExportProperties = {
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
    this.pivotObj.grid.excelExport(excelExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Changing the file name while exporting

The Excel export provides an option to change file name of the document before exporting. In-order to change the file name, define **fileName** property in **excelExportProperties** object and pass it as a parameter to the [`excelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#excelexport) method.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ExcelExportProperties } from '@syncfusion/ej2-grids';

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    let excelExportProperties: ExcelExportProperties = {
      fileName: 'sample.xlsx'
    };
    this.pivotObj.grid.excelExport(excelExportProperties);
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## CSV Export

The Excel export allows pivot table data to be exported in **CSV** file format as well. To enable CSV export in the pivot table, set the [`allowExcelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowexcelexport) property in [`PivotView`](https://ej2.syncfusion.com/react/documentation/api/pivotview) as **true**. Once the API is set, user needs to call the [`csvExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#csvexport) method for exporting on external button click.

> The pivot table component can be exported to CSV format using options available in the toolbar. For more details [`refer`](./tool-bar) here.

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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.csvExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Virtual Scroll Data

You can export the pivot table virtual scroll data as Excel/CSV document by using PivotEngine export without any performance degradation. To enable PivotEngine export in the pivot table, set the [`allowExcelExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview#allowexcelexport) as true. You need to use the `exportToExcel` method for PivotEngine export.

> To use PivotEngine export, You need to inject the `ExcelExport` module in pivot table.
> PivotEngine export will be performed while enabling virtual scrolling by default.

### Virtual Scroll Data Excel Export

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, Inject, ExcelExport } from '@syncfusion/ej2-react-pivotview';
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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}><Inject services={[ExcelExport]} /></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.excelExportModule.exportToExcel('Excel');
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Virtual Scroll Data CSV Export

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, Inject, ExcelExport } from '@syncfusion/ej2-react-pivotview';
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
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowExcelExport={true}><Inject services={[ExcelExport]} /></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.excelExportModule.exportToExcel('csv');
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Events

### ExcelQueryCellInfo

The event `excelQueryCellInfo` triggers while framing each row and value cell during Excel export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `value` - It holds the cell value.
* `column` -  It holds column information for the current cell.
* `data` - It holds the entire row data across the current cell.
* `style`  - It holds the style properties for the cell.

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
    excelQueryCellInfo: this.excelQueryCellInfo.bind(this)
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
  excelQueryCellInfo(args: ExcelQueryCellInfoEventArgs): void {
    //triggers every time for header cell while rendering
  }
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }
   btnClick(): void {
    this.pivotObj.excelExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

### ExcelHeaderQueryCellInfo

The event `excelHeaderQueryCellInfo` triggers on framing each header cell during Excel export. It allows the user to customize the cell value, style etc. of the current cell. It has the following parameters:

* `cell` - It holds the current cell information.
* `style`  -  It holds the style properties for the cell.

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
    excelHeaderQueryCellInfo: this.excelHeaderQueryCellInfo.bind(this)
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
  excelHeaderQueryCellInfo(args: ExcelHeaderQueryCellInfoEventArgs): void {
    //triggers every time for header cell while rendering
  }
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} gridSettings={this.gridSettings} dataSourceSettings={this.dataSourceSettings} allowPdfExport={true}></PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Export</ButtonComponent></div></div>
  }
   btnClick(): void {
    this.pivotObj.excelExport();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## See Also

* [PDF Exporting](./pdf-export)