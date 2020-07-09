---
title: "Editing"
component: "Pivot Table"
description: "Editing allows to perform CRUD operation in the raw items of any cells of the pivot table."
---

# Editing

> This feature is applicable only for the relational data source.

Cell edit allows to add, delete, or update the raw items of any value cell from the pivot table. The raw items can be viewed in a data grid inside a new window on double-clicking the appropriate value cell. In the data grid, CRUD operations can be performed by double-clicking the cells or using toolbar options. Once user finishes editing raw items, aggregation will be performed for the updated values in pivot table component immediately. This support can be enabled by setting the [`allowEditing`](https://ej2.syncfusion.com/react/documentation/api/pivotview/cellEditSettingsModel/#allowediting) property in [`cellEditSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#editsettings) to **true**.

The CRUD operations available in the data grid toolbar and command column are:

| Toolbar Button | Actions |
|----------------|---------|
| Add | Add a new row.|
| Edit | Edit the current row or cell.|
| Delete | Delete the current row.|
| Update | Update the edited row or cell.|
| Cancel | Cancel the edited state. |

The following are the supported edit types in the data grid:

* Normal
* Dialog
* Batch
* Command Columns

## Normal

In normal edit mode, when user starts editing, the state of the currently selected row alone will be completely changed to edit state. User can change the cell values and save it to the data source by clicking "Update" toolbar button. To enable the normal edit, set the [`mode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/cellEditSettingsModel/#mode) property in [`cellEditSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#editsettings) to **Normal**.

> The normal edit mode **Normal** is set as the default mode for editing.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, CellEditSettings, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public editSettings: CellEditSettings = {
    allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'
  } as CellEditSettings

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} editSettings={this.editSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

> The normal edit mode is the default mode of editing.

## Dialog

In dialog edit mode, when user starts editing, the currently selected row data will be shown in an exclusive dialog. User can change cell values and save it to the data source by clicking "Save" button in the dialog. To enable the dialog edit, set the [`mode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/cellEditSettingsModel/#mode) property in [`cellEditSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#editsettings) to **Dialog**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, CellEditSettings, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public editSettings: CellEditSettings = {
    allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Dialog'
  } as CellEditSettings

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} editSettings={this.editSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Batch

In batch edit mode, when user double-clicks any data grid cell, the state of target cell is changed to edit state. User can perform bulk changes and finally save (added, changed, and deleted data in the single request) to the data source by clicking "Update" toolbar button. To enable the batch edit, set the [`mode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/cellEditSettingsModel/#mode) property in [`cellEditSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#editsettings) to **Batch**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, CellEditSettings, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public editSettings: CellEditSettings = {
    allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Batch'
  } as CellEditSettings

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} editSettings={this.editSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Command column

An additional column appended in the data grid layout holds the command buttons to perform the CRUD operation. To enable the command columns, set the [`allowCommandColumns`](https://ej2.syncfusion.com/react/documentation/api/pivotview/cellEditSettingsModel/#allowcommandcolumns) property in [`cellEditSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#editsettings) to **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, CellEditSettings, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public editSettings: CellEditSettings = {
    allowAdding: true, allowDeleting: true, allowEditing: true, allowCommandColumns: true
  } as CellEditSettings

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} editSettings={this.editSettings} ></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Editing using the pivot chart

Users can also add, delete, or update the underlying raw items of any data point via pivot chart. The raw items will be shown in the data grid in the new window by clicking the appropriate data point. Then you can edit the raw items as mentioned above by any of the edit types (normal, dialog, batch and command column).

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { CellEditSettings, IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public editSettings: CellEditSettings = {
    allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Normal'
  } as CellEditSettings

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: { type: 'Column' }
  } as ChartSettings;

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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} editSettings={this.editSettings}><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Events

### DrillThrough

For more information [`refer`](./drill-through/#drillthrough) here.

### BeginDrillThrough

For more information [`refer`](./drill-through/#begindrillthrough) here.

## See Also

* [Configure data grid-options on editing](./how-to/configure-data-grid-options-on-editing-mode)