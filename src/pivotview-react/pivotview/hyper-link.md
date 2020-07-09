---
title: "Hyperlink"
component: "Pivot Table"
description: "User allows to show hyperlink option to the link data for individual cells."
---

# Hyperlink

The pivot table supports to show hyperlink option to link data for individual cells that are displayed in the component. Also, the hyperlink can be enabled separately for row headers, column headers, value cells, and summary cells using the [`hyperlinkSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#hyperlinksettings). It can be configured through code behind, during initial rendering and the settings available to show hyperlink are:

* [`showHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showhyperlink): It allows to set the visibility of hyperlink in all cells.
* [`showRowHeaderHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showrowheaderhyperlink): It allows to set the visibility of hyperlink in row headers.
* [`showColumnHeaderHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showcolumnheaderhyperlink): It allows to set the visibility of hyperlink in column headers.
* [`showValueCellHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showvaluecellhyperlink): It allows to set the visibility of hyperlink in value cells.
* [`showSummaryCellHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showsummarycellhyperlink): It allows to set the visibility of hyperlink in summary cells.
* [`headerText`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#headertext): It allows to set the visibility of hyperlink based on header text.
* [`conditionalSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#conditionalsettings): It allows to set the visibility of hyperlink based on specific condition.

> By default, the hyperlink options are disabled for all cells in the pivot table.
>
> User defined style can be applied to hyperlink using [`cssClass`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#cssclass) property in [`hyperlinkSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#hyperlinksettings).

## Hyperlink for all cells

The pivot table has an option to show hyperlink option for all cells that are currently in display. To do so, user need to set [`showHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showhyperlink) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    showHyperlink: true,
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Hyperlink for row headers

The pivot table has an option to show hyperlink option for row header cells alone that are currently in display. To do so, user need to set [`showRowHeaderHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showrowheaderhyperlink) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    showRowHeaderHyperlink: true,
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Hyperlink for column headers

The pivot table has an option to show hyperlink option for column header cells alone that are currently in display. To do so, user need to set [`showColumnHeaderHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showcolumnheaderhyperlink) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    showColumnHeaderHyperlink: true,
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Hyperlink for value cells

The pivot table has an option to show hyperlink option for value cells alone that are currently in display. To do so, user need to set [`showValueCellHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showvaluecellhyperlink) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperlinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    showValueCellHyperlink: true,
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Hyperlink for summary cells

The pivot table has an option to show hyperlink option for summary cells alone that are currently in display. To do so, user need to set [`showSummaryCellHyperlink`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#showsummarycellhyperlink) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    showSummaryCellHyperlink: true,
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Condition based hyperlink

The pivot table has an option to show hyperlink option to the cells based on specific conditions. It can be configured using the [`conditionalSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#conditionalsettings) option through code behind, during initial rendering. The settings required to sort are:

* [`measure`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalSettingsModel/#measure): Specifies the value field name to get visibility of hyperlink option for specific measure.
* [`conditions`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalSettingsModel/#conditions): Specifies the operator type such as equals, greater than, less than, etc.
* [`value1`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalSettingsModel/#value1): Specifies the start value.
* [`value2`](https://ej2.syncfusion.com/react/documentation/api/pivotview/conditionalSettingsModel/#value2): Specifies the end value.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    conditionalSettings: [{
        measure: 'Sold',
        conditions: 'Between',
        value1: 150,
        value2: 500
    }],
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Header based hyperlink

The pivot table has an option to show hyperlink in the cells based on specific row or column header. It can be configured using the [`headerText`](https://ej2.syncfusion.com/react/documentation/api/pivotview/hyperlinkSettingsModel/#headertext) option through code behind, during initial rendering.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { HyperLinkSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/hypderlinksettings';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    enableSorting: true,
    drilledMembers: [{ name: 'Year', items: ['FY 2015'] }, { name: 'Country', items: ['France'] }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    filters: []
  }
  public hyperlinkSettings: HyperLinkSettings = {
    headerText: 'FY 2015.Q1.Units Sold',
    cssClass: 'e-custom-class'
  } as HyperLinkSettings;
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings} hyperlinkSettings={this.hyperlinkSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Event

The event [`hyperlinkCellClick`](https://ej2.syncfusion.com/react/documentation/api/pivotview#hyperlinkcellclick) fires on every hyperlink cell click.

It has following parameters - `Cancel` and `CurrentCell`. The parameter `CurrentCell` is used to customize the host cell element by any means. Meanwhile, when the parameter `Cancel` is set to **true**, applied customization will not be updated to the host cell element.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList, IDataOptions, IDataSet, Inject, PivotViewComponent, HyperCellClickEventArgs } from '@syncfusion/ej2-react-pivotview';
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
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} hyperlinkCellClick={this.hyperlinkCellClick.bind(this)} showFieldList={true}><Inject services={[FieldList]} /></PivotViewComponent>
  }

  hyperlinkCellClick(args: HyperCellClickEventArgs): void  {
      args.cancel = false;
      args.currentCell.setAttribute("data-url", "https://ej2.syncfusion.com/");//here we have redirected to EJ2 Syncfusion on hyperlinkcell click
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## See Also

* [Apply condition based hyperlink for specific row or column](./how-to/apply-condition-based-hyper-link-for-specific-row-or-column)