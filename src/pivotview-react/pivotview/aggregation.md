---
title: "Aggregation"
component: "Pivot Table"
description: "Aggregation allows user to summarize the measure values."
---

# Aggregation

> This feature is applicable only for the relational data source.

End user can perform calculations over a group of values (exclusively for value fields bound in value axis) using the aggregation option. By default, values are added (summed) together. The other aggregation types are explained below.

> The fields with data type such as number support all aggregation types mentioned below except for **"CalculatedField"**. The fields with data type such as string, date, datetime, boolean, etc., support **"Count"** and **"DistinctCount"** aggregation types alone.

| Operator | Description |
|------|-------------|
| Sum| Displays the pivot table values with sum.|
| Product| Displays the pivot table values with product.|
| Count| Displays the pivot table values with count.|
| DistinctCount| Displays the pivot table values with distinct count.|
| Min| Displays the pivot table with minimum value.|
| Max| Displays the pivot table with maximum value.|
| Avg| Displays the pivot table values with average.|
| Index| Displays the pivot table values with index.|
| PopulationStDev| Displays the pivot table values with standard deviation of population.|
| SampleStDev| Displays the pivot table values with sample standard deviation.|
| PopulationVar| Displays the pivot table values with variance of population.|
| SampleVar| Displays the pivot table values with sample variance.|
| RunningTotals| Displays the pivot table values with running totals.|
| DifferenceFrom| Displays the pivot table values with difference from the value of the base item in the base field.|
| PercentageOfDifferenceFrom| Displays the pivot table values with percentage difference from the value of the base item in the base field.|
| PercentageOfGrandTotal| Displays the pivot table values with percentage of grand total of all values.|
| PercentageOfColumnTotal| Displays the pivot table values in each column with percentage of total values for the column.|
| PercentageOfRowTotal| Displays the pivot table values in each row with percentage of total values for the row.|
| PercentageOfParentTotal| Displays the pivot table values with percentage of total of all values based on selected field.|
| PercentageOfParentColumnTotal| Displays the pivot table values with percentage of its parent total in each column.|
| PercentageOfParentRowTotal| Displays the pivot table values with percentage of its parent total in each row.|
| CalculatedField| Displays the pivot table with calculated field values. It allows user to create a new calculated field alone.|

## Assigning aggregation type for value fields through API

For each value field, the aggregation type can be set using the property [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#type) in [`values`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#values) class. Meanwhile, aggregation types like **DifferenceFrom** and **PercentageOfDifferenceFrom** can check for specific field of specific item using [`baseField`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#basefield) and [`baseItem`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#baseitem) properties. Likewise, **PercentageOfParentTotal** type can for specific field using [`baseField`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#basefield) property. For instance, the aggregation type **DifferenceFrom** would intake the specified field and its corresponding member as input and its value is compared across other members in the same field and also across different fields to formulate an appropriate output value.  

* [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#type): It allows to set the aggregate type of the field.
* [`baseField`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#basefield): It allows to set the specific field to aggregate the values.
* [`baseItem`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#baseitem): It allows to set the specific member to aggregate the values.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

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
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount', type: 'Sum' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

> By default, the aggregation will be considered as **Sum** to the value fields which had number type and for the value fields which had non-number type values such as string, date, datetime, boolean, etc., the aggregation type will be considered as **Count**.

## Modifying aggregation type for value fields at runtime

Aggregation types can be changed easily through UI at runtime. The value fields bound to grouping bar and field list appears with a dropdown icon which helps to select an appropriate aggregation type for the respective value field. On selection, the values in the pivot table will be changed dynamically.

<!-- markdownlint-disable MD012 -->
![output](images/aggregation_fl_menu.png "List of pre-defined aggregation types to be changed via Field List")
<br/>
<br/>
![output](images/aggregation_gb_menu.png "List of pre-defined aggregation types to be changed via Grouping Bar")

## Show desired aggregation types in its dropdown menu

By default, all the aggregation types are displayed in the dropdown menu available in buttons. However, based on the request for an application, we may need to show selective aggregation types on our own. This can be achieved using the [`aggregateTypes`](https://ej2.syncfusion.com/react/documentation/api/pivotview#aggregatetypes) property.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { GroupingBar, FieldList, Inject, IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: pivotData as IDataSet,
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount', type: 'Sum' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    filters: [],
  }
  public pivotObj: PivotViewComponent;
  public pivotAggregateTypes: any = ['DistinctCount', 'Avg', 'Product'];
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showFieldList={true} showGroupingBar={true} aggregateTypes={this.pivotAggregateTypes}><Inject services={[GroupingBar, FieldList]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Hiding aggregation type from button text

By default, in value axis each field would be displayed by its name and aggregation type together. To hide aggregation type and display field name alone, set the property [`showAggregationOnValueField`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#showaggregationonvaluefield)  in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/) to **false**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, GroupingBar } from '@syncfusion/ej2-react-pivotview';
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
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount', type: 'Sum' }],
    showAggregationOnValueField: false
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings} showGroupingBar={true}><Inject services={[GroupingBar]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Hiding aggregation type icon from UI

By default, the icon to set aggregation type is enabled in the grouping bar. To disable this icon, set the property [`showValueTypeIcon`](https://ej2.syncfusion.com/react/documentation/api/pivotview/groupingBarSettingsModel/#showvaluetypeicon) in [`groupingBarSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#groupingbarsettings) to **false**.

> Icon to change the aggregation type can be hidden only in Grouping Bar but not in Field List at the moment.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { GroupingBar, GroupingBarSettings,  IDataOptions, IDataSet, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{
  public groupingSettings: GroupingBarSettings = {
    showValueTypeIcon: false
  } as GroupingBarSettings;

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
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} groupingBarSettings={this.groupingSettings} dataSourceSettings={this.dataSourceSettings} showGroupingBar={true} ><Inject services={[GroupingBar]}/> </PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

## Event

### AggregateCellInfo

The event [`aggregateCellInfo`](https://ej2.syncfusion.com/documentation/api/pivotview#aggregatecellinfo) triggers every time while rendering each value cell. This allows user to change the cell value and skip formatting if applied. It has following parameters:

* `fieldName` - It holds current cell's field name.
* `row` - It holds current cell's row value.
* `column` - It holds current cell's row value.
* `value` - It holds value of current cell.
* `cellSets` - It holds raw data for the aggregated value cell.
* `rowCellType` - It holds row cell type value.
* `columnCellType` - It holds column cell type value.
* `aggregateType` - It holds aggregate type of the cell.
* `skipFormatting` - boolean property, it allows to skip formatting if applied.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, AggregateEventArgs } from '@syncfusion/ej2-react-pivotview';
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

  aggregateCell(args: AggregateEventArgs): void {
      args.skipFormatting = true;
  }

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} aggregateCellInfo={this.aggregateCell.bind(this)} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}
