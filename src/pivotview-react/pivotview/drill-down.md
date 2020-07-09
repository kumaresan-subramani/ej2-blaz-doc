---
title: "Drill Operation"
component: "Pivot Table"
description: "Expand or collapse headers displayed in rows and columns."
---

# Drill Down

## Drill down and drill up

The drill down and drill up action helps to view the bound data in detailed and abstract view respectively. By default, if member(s) has children, then expand and collapse icon will be displayed in the respective row/column header. On clicking the icon, expand or collapse action will be performed automatically through built-in source code. Meanwhile, leaf member(s) does not contain expand and collapse icon.

![output](images/drill.png)

## Drill position

Allows to drill only the current position of the selected member and exclude the drilled data of selected member in other positions. For example, if "FY 2015" and "FY 2016" have "Quarter 1" member as child in next level, and when end user attempts to drill "Quarter 1" under "FY 2016", only it will be expanded and not "Quarter 1" under "FY 2015".

> This feature is built-in and occurs every time when expand or collapse action is done for better performance.

![output](images/drill_position.png)

## Expand all

> This property is applicable only for the relational data source.

Allows to either expand or collapse all headers that are displayed in row and column axes. To display all headers in expanded state, set the property [`expandAll`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#expandall) to **true** and to collapse all
headers, set the property [`expandAll`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#expandall) to **false**. By default, [`expandAll`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#expandall) property is set to **false**.

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
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Expand all except specific member(s)

> This option is applicable only for the relational data source.

In addition to the previous topic, there is an enhancement to expand all headers expect specific header(s) and similarly to collapse all headers except specific header(s). To achieve this, [`drilledMembers`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#drilledmembers) is used. The required properties of the [`drilledMembers`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#drilledmembers) are explained below:

* [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/drillOptionsModel/#name): It allows to set the field name whose member(s) needs to be specifically drilled.
* [`items`](https://ej2.syncfusion.com/react/documentation/api/pivotview/drillOptionsModel/#items): It allows to set the exact member(s) which needs to be drilled.

> The [`drilledMembers`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#drilledmembers) option always works in vice-versa with respect to the property [`expandAll`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#expandall) in pivot table. For example, if [`expandAll`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#expandall) is set to **true**, then the member(s) added in [`items`](https://ej2.syncfusion.com/react/documentation/api/pivotview/drillOptionsModel/#items) collection alone will be in collapsed state.

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
    expandAll: true,
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Expand specific member(s)

End user can also manually expand or collapse specific member(s) in each fields under row and column axes using the [`drilledMembers`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#drilledmembers) from code behind. The required properties of the [`drilledMembers`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#drilledmembers) are explained below:

* [`name`](https://ej2.syncfusion.com/react/documentation/api/pivotview/drillOptionsModel/#name): It allows to set the field name whose member(s) needs to be specifically drilled.
* [`items`](https://ej2.syncfusion.com/react/documentation/api/pivotview/drillOptionsModel/#items): It allows to set the exact member(s) which needs to be drilled.
* [`delimiter`](https://ej2.syncfusion.com/react/documentation/api/pivotview/drillOptionsModel/#delimiter): It allows to separate next level of member from its parent member.

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
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Event

### Drill

The event [`drill`](https://ej2.syncfusion.com/react/documentation/api/pivotview#aggregatecellinfo) triggers every time when a field is expanded or collapsed. For instance using this event user can alter delimiter and drill action for the respective item. It has the following parameters:

* `drillInfo` - It holds the current drilled item information.
* `pivotview` - It holds pivot table instance.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, DrillArgs } from '@syncfusion/ej2-react-pivotview';
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
    formatSettings: [{ name: 'Amount', format: 'C2'}],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }
  public pivotObj: PivotViewComponent;

  drill(args: DrillArgs): void {
      args.dataSourceSettings.columns[0].caption = "Full Year";
      args.dataSourceSettings.expandAll = true;
  }

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} drill={this.drill.bind(this)} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}