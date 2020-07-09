---
title: "Tooltip"
component: "Pivot Table"
description: "Describes about enabling and disabling tooltip in pivot table"
---

# Tooltip

The tooltip can be enabled or disabled by setting the [`showTooltip`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#showtooltip) property to **true**. By default, tooltip is enabled in the pivot table.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
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
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} showTooltip={true} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Tooltip Template

User can design their own tooltip by setting the property [`tooltipTemplate`](https://ej2.syncfusion.com/react/documentation/api/pivotview#tooltiptemplate) with own HTML elements. The property accepts both HTML string and ID attribute. The following place holders are available to display its dynamic values inside the HTML elements.

`${rowHeaders}` – Row headers of the selected value cell.

`${columnHeaders}`  – Column headers of the selected value cell.

`${rowFields}` – Row fields of the selected value cell.

`${columnFields}` – Column fields of the selected value cell.

`${valueField}` – Field name of the selected value cell.

`${aggregateType}` – Aggregate type of the selected value cell.

`${value}` - Formatted value of the selected value cell.

The tooltip customization is common for both pivot table and pivot chart or it can be done individually as well. To customize the pivot table tooltip, the above procedure needs to be followed. To customize the pivot chart tooltip alone use `template` property of tooltip under [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettings).

In the below sample, the pivot table and pivot chart shows customized tooltip layouts.

{% tab template="pivot-table/tooltipTemplate", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, Inject, PivotViewComponent, Toolbar } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{
  public toolbarOptions: any = ['Grid', 'Chart'];

  public chartSettings: ChartSettings = {
      chartSeries: { type: 'Column', animation: { enable: false } },
      tooltip:{ template:'<span class="wrap">${aggregateType} of ${valueField}: ${value}</span>' }
  } as ChartSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    filters: []
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} showTooltip={true} dataSourceSettings={this.dataSourceSettings} chartSettings={this.chartSettings} displayOption={{ view: 'Both' }} showToolbar={true} tooltipTemplate={"#Template"} toolbar={this.toolbarOptions}><Inject services={[Toolbar]} /></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}