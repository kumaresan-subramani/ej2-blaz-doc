---
title: "Summary Customization"
component: "Pivot Table"
description: "Show/hide sub-totals and grand totals for the pivot table"
---

# Show or hide totals

## Show or hide grand totals

Allows to show or hide grand totals in rows and columns using the [`showGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showgrandtotals) property. To hide the grand totals in rows and columns, set the property [`showGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showgrandtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#datasourcesettings) to **false**.
End user can also hide grand totals for row or columns separately by setting the property [`showRowGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showrowgrandtotals) or [`showColumnGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showcolumngrandtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#datasourcesettings) to **false** respectively.

> By default, [`showGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showgrandtotals), [`showRowGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showrowgrandtotals) and [`showColumnGrandTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showcolumngrandtotals) properties in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#datasourcesettings) are set as **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList,  IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
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
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    showGrandTotals: false
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true} ><Inject services={[FieldList]}/> </PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Show or hide sub-totals

Allows to show or hide sub-totals in rows and columns using the [`showSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showsubtotals) property. To hide all the sub-totals in rows and columns, set the property [`showSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showsubtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#datasourcesettings) to **false**. End user can also hide sub-totals for rows or columns separately by setting the property [`showRowSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showrowsubtotals) or [`showColumnSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showcolumnsubtotals) in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#datasourcesettings) to **false** respectively.

> By default, [`showSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showsubtotals), [`showRowSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showrowsubtotals) and [`showColumnSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showcolumnsubtotals) properties in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#datasourcesettings) are set as **true**.

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
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    showSubTotals: false
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true} ><Inject services={[FieldList]}/> </PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Show or hide sub-totals for specific fields

Allows to show or hide sub-totals for specific fields in rows and columns using the [`showSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showsubtotals) property. To hide sub-totals for a specific field in row or column axis, set the property [`showSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showsubtotals) in [`row`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#rows) or [`column`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#columns) to **false** respectively.

> By default, [`showSubTotals`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#showsubtotals) property in [`row`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#rows) or [`column`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#columns) is set as **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { FieldList,  IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year', showSubTotals: false }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country', showSubTotals: false }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true} ><Inject services={[FieldList]}/> </PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Show or hide totals using toolbar

It can also be achieved using built-in toolbar options by setting the [`showToolbar`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#showtoolbar) property to **true**. Also, include the items **GrandTotal** and **SubTotal** within the [`toolbar`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#toolbar) property. End user can now see "Show/Hide Grand totals" and "Show/Hide Sub totals" icons in toolbar UI automatically.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import {
    PivotViewComponent, IDataOptions, Toolbar, Inject
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
   public toolbarOptions: any = ['SubTotal', 'GrandTotal'];
  render() {
    return <PivotViewComponent id='PivotView' ref={(scope) => { this.pivotObj = scope; }} dataSourceSettings={this.dataSourceSettings} width={'100%'} height={350} gridSettings={{ columnWidth: 140 }} showToolbar={true} displayOption={{ view: 'Both' }} toolbar={this.toolbarOptions}><Inject services={[Toolbar]} /></PivotViewComponent>
  }
};
ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}