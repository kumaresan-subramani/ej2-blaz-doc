---
title: "Number Formatting"
component: "Pivot Table"
description: "Number Formatting allows user to formatting numeric values in pivot table."
---

# Number Formatting

Allows you to specify the required display format that should be used in values of the pivot table. Supported display formats are:

* Number
* Currency
* Percentage
* Custom

You can apply format for the numeric values using the following properties in the [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#formatsettings).

* [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#name): It allows to specify the field name.
* [`format`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#format): It allows to specify the format of the respective field.

Possible formatting values are:

1. N - denotes numeric type.
2. C - denotes currency type.
3. P - denotes percentage type.

> If no format is specified it takes number as default format type.

Other properties include:

* [`useGrouping`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#usegrouping): It allows to enable or disable the separator, for example, $100,000,000 or $100000000 respectively. By default, it will be set as **true**.
* [`currency`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#currency): It allows to set the currency code which needs to considered for the currency formatting.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    allowLabelFilter: true,
    allowValueFilter: true,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2', useGrouping: false, currency: 'EUR' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true}><Inject services={[FieldList]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

You can also format the values at runtime using the formatting dialog. This option can be enabled by setting the [`allowNumberFormatting`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#allownumberformatting) property to **true**. The same has been discussed in some of the upcoming topics.

> To use the formatting dialog, inject the `NumberFormatting` module into the pivot table.

## Custom format

You can add any custom format directly to the [`format`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#format) property in the [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#formatsettings). Custom format can be achieved by using one or more format specifiers listed in the below table.

| Specifier | Description | Input | Format Output |
| ------- |--------------- | ---------------- | --------------- |
| 0 | Replaces the zero with the corresponding digit if it is present. Otherwise, zero will appear in the result string. | { format: '0000' } | '0123' |
| # | Replaces the ' # ' symbol with the corresponding digit if it is present. Otherwise, no digits will appear in the result string.| { format: '####' } | '1234' |
| . | Denotes the number of digits permitted after the decimal point. | { format: '###0.##0#' } | '546321.000' |
| % | Percent specifier denotes the percentage type format. | { format: '0000 %' } | '0100 %' |
| $ | Denotes the currency type format that is based on the global currency code specified. | { format: '$ ###.00' } | '$ 13.00' |
| ; | Denotes separate formats for positive, negative and zero values. | { format: '###.##;(###.00);-0' } | '(120.00)'    |
| 'String' (single Quotes) | Denotes the characters that are enclosed in the single quote (') to be replaced in the resulting string. | { format: "####.00 '@'" } | "123.00 @"    |

>NOTE: If custom format is defined, certain properties such as [`useGrouping`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#usegrouping) and [`currency`](https://ej2.syncfusion.com/react/documentation/api/pivotview/formatSettingsModel/#currency) will not be considered.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    allowLabelFilter: true,
    allowValueFilter: true,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Sold', format: "####.00 'Nos'" }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true}><Inject services={[FieldList]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Toolbar

You can enable formatting dialog option in the toolbar by adding `NumberFormatting` in the [`toolbar`](../../api/pivotview/#toolbar). After that, you can see the option to invoke the formatting dialog in the toolbar.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import {
    PivotViewComponent, IDataOptions, Inject, FieldList, CalculatedField,
    Toolbar, PDFExport, ExcelExport, ConditionalFormatting, SaveReportArgs,
    FetchReportArgs, LoadReportArgs, RemoveReportArgs, RenameReportArgs, NumberFormatting
} from '@syncfusion/ej2-react-pivotview';
import { pivotData } from './datasource';
class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  };
  public pivotObj: PivotViewComponent;
   public toolbarOptions: any = ['New', 'Save', 'SaveAs', 'Rename', 'Remove', 'Load',
        'Grid', 'Chart', 'Export', 'SubTotal', 'GrandTotal', 'ConditionalFormatting', 'NumberFormatting', 'FieldList'];


    saveReport(args: any): void {
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
    }
    fetchReport(args: FetchReportArgs): void {
        let reportCollection: string[] = [];
        let reeportList: string[] = [];
        if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
            reportCollection = JSON.parse(localStorage.pivotviewReports);
        }
        reportCollection.map(function (item: any): void { reeportList.push(item.reportName); });
        args.reportName = reeportList;
    }
    loadReport(args: LoadReportArgs): void {
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
            this.pivotObj.dataSource = JSON.parse(args.report).dataSource;
        }
    }
    removeReport(args: RemoveReportArgs): void {
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
    }
    renameReport(args: RenameReportArgs): void {
        let reportCollection: string[] = [];
        if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
            reportCollection = JSON.parse(localStorage.pivotviewReports);
        }
        reportCollection.map(function (item: any): any { if (args.reportName === item.reportName) { item.reportName = args.rename; } });
        if (localStorage.pivotviewReports && localStorage.pivotviewReports !== "") {
            localStorage.pivotviewReports = JSON.stringify(reportCollection);
        }
    }
    newReport(): void {
        this.pivotObj.setProperties({ dataSource: { columns: [], rows: [], values: [], filters: [] } }, false);
    }
  render() {
    return <PivotViewComponent id='PivotView' ref={(scope) => { this.pivotObj = scope; }} dataSourceSettings={this.dataSourceSettings} width={'100%'} height={350} showFieldList={true} gridSettings={{ columnWidth: 140 }} allowExcelExport={true} allowConditionalFormatting={true} allowNumberFormatting={true} allowPdfExport={true} showToolbar={true} allowCalculatedField={true} displayOption={{ view: 'Both' }} toolbar={this.toolbarOptions} newReport={this.newReport.bind(this)} renameReport={this.renameReport.bind(this)} removeReport={this.removeReport.bind(this)} loadReport={this.loadReport.bind(this)} fetchReport={this.fetchReport.bind(this)} saveReport={this.saveReport.bind(this)}><Inject services={[FieldList, CalculatedField, Toolbar, PDFExport, ExcelExport, ConditionalFormatting, NumberFormatting]} /></PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Invoking formatting dialog through external button

You can invoke the formatting dialog by clicking an external button using the `ShowNumberFormattingDialog` method.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CalculatedField, IDataOptions, IDataSet, Inject, PivotViewComponent, NumberFormatting } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Units', type: 'CalculatedField' }],
    calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} allowNumberFormatting={true}><Inject services={[CalculatedField, NumberFormatting]}/> </PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Number Formatting</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.numberFormattingModule.showNumberFormattingDialog();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Events

### NumberFormatting

The event [`numberFormatting`](https://ej2.syncfusion.com/react/documentation/api/pivotview#numberformatting) fires while closing the number formatting dialog on "OK" button click. It allows the user to restrict the customization settings done by the user. It has the following parameters

* `formatName`: It holds the name of the field.

* [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#formatsettings): It holds the [`formatSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#formatsettings) property of the pivot report.

* `cancel`: It is a boolean property and by setting this to true , the customization done in number formatting dialog won’t be applied.

In the below sample, the customization done in number formatting dialog for the field "Amount" won’t be applied.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CalculatedField, IDataOptions, IDataSet, Inject, PivotViewComponent, NumberFormatting, NumberFormattingEventArgs } from '@syncfusion/ej2-react-pivotview';
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
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, { name: 'Total', caption: 'Total Units', type: 'CalculatedField' }],
    calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Sold)"' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <div><div className="col-md-9"> <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} allowCalculatedField={true} allowNumberFormatting={true}numberFormatting={this.numberFormatting.bind(this)}><Inject services={[CalculatedField, NumberFormatting]}/> </PivotViewComponent></div>
    <div className='col-lg-3 property-section'><ButtonComponent cssClass='e-primary' onClick={this.btnClick.bind(this)}>Number Formatting</ButtonComponent></div></div>
  }

  btnClick(): void {
    this.pivotObj.numberFormattingModule.showNumberFormattingDialog();
  }

  numberFormatting (args: NumberFormattingEventArgs): void {
    if(args.formatName === 'Amount') {
            args.cancel = true;
        }
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## See Also

* [Customize number, date, and time values](./how-to/customize-number-date-and-time-values.md)
* [NumberFormatOptions](https://ej2.syncfusion.com/react/documentation/common/intl.html?lang=typescript#manipulating-numbers)
* [Toolbar](./tool-bar)