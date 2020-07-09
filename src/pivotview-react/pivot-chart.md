---
title: "Pivot Chart"
component: "Pivot Table"
description: "It allows the user to display a pivot chart component based on the pivot report bound on it. And the UI of the pivot chart component can be customized."
---

# Pivot Chart

In pivot table component, pivot chart would act as an additional visualization component with its basic and important characteristic like drill down and drill up, 15+ chart types, series customization, axis customization, legend customization, export, print and tooltip. Its main purpose is to show the pivot data in graphical format.

If user prefers, the pivot chart component can also be displayed individually with pivot values and can change the report dynamically with the help of field list and grouping bar. Using the [`displayOption`](https://ej2.syncfusion.com/react/documentation/api/pivotview#displayoption) property, user can set the visibility of grid and chart in pivot table component. It holds below properties,

* [`view`](https://ej2.syncfusion.com/react/documentation/api/pivotview/displayOptionModel/#view): Specifies the pivot table component to display grid alone or chart alone or both.
* [`primary`](https://ej2.syncfusion.com/react/documentation/api/pivotview/displayOptionModel/#primary): Specifies the pivot table to display either grid or chart as primary component during initial loading. It is applicable only when setting the property [`view`](https://ej2.syncfusion.com/react/documentation/api/pivotview/displayOptionModel/#view) to **Both**.

> You should inject the PivotChart module to make the its features available in the pivot table.

The below sample displays the pivot chart component based on the pivot report bound on it.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Data Binding

End user can bind both local and remote data binding options available in the component to feed the data. The [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#datasource) property can be assigned either with an instance of `DataManager` or JavaScript object array collection.
For more information [`refer`](./data-binding) here.

## Chart Types

Supports 19 different types of charts as follows,

* Line
* Column
* Area
* Bar
* StepArea
* StackingColumn
* StackingArea
* StackingBar
* StepLine
* Pareto
* Bubble
* Scatter
* Spline
* SplineArea
* StackingColumn100
* StackingBar100
* StackingArea100
* Polar
* Radar

**Line** is the default pivot chart type. User can change the pivot chart type by using the property [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/#type) in [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#chartseries) class.

In the below code sample, the pivot chart type is set as **Bar**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: { type: 'Bar' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Accumulation Charts

Supports 4 different types of accumulation charts as follows,

* Pie
* Doughnut
* Funnel
* Pyramid

As like other chart types it can be changed using the property [`type`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/#type) in [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/).

In the below code sample, the **Pie** chart is rendered, and the other accumulation charts can be switched using the drop-down list.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import { DropDownListComponent } from '@syncfusion/ej2-react-dropdowns';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        chartSeries: { type: 'Pie' }
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

    public chartTypes = [
        { 'value': 'Pie', 'text': 'Pie' },
        { 'value': 'Doughnut', 'text': 'Doughnut' },
        { 'value': 'Funnel', 'text': 'Funnel' },
        { 'value': 'Pyramid', 'text': 'Pyramid' },
    ];
    public pivotObj: PivotViewComponent;
    ddlOnChange(args) {
        this.pivotObj.chartSettings.chartSeries.type = args.value;
    }
    render() {
    return <div><div className="container" style={{ height: '500px' }}><div id="dropdown-control" style={{marginBottom: '5px'}}><table style={{width: '350px', marginLeft: '50px'}}><tbody><tr  style={{ height: '50px' }} ><td><div><b>Accumulation Chart:</b></div></td><td><div><DropDownListComponent  floatLabelType={'Auto'} fields={this.fields} change={this.ddlOnChange.bind(this)} id="charttypes" index={0} enabled={true} dataSource={this.chartTypes}/></div></td></tr></tbody></table></div><div><PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent></div></div>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));
```

{% endtab %}

### Drill Down/Up

In the accumulation charts, drill down and drill up operations can be performed using the built-in context menu option. It will be shown while clicking on the chart series. The context menu has the following options:
**Expand** - It is to drill down the corresponding series until the last level.
**Collapse** - It is to drill up the corresponding series until the first level.
**Exit** - It is to close the context menu.

> The drill operation in accumulation charts can be performed only for row headers.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        chartSeries: { type: 'Pie' }
    } as ChartSettings;

    public dataSourceSettings: IDataOptions = {
        columns: [{ name: 'Products' }],
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        filters: [],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        rows: [{ name: 'Country' }, { name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
    }

    public pivotObj: PivotViewComponent;
    render() {
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>  
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

![output](images/expand_collapse.png)

### Column Headers and Delimiters

Unlike other chart types, the accumulation charts consider the values of a single column from the pivot table to be drawn. Preferably the first column of the pivot table is considered by default. But it can be changed by defining the column headers using the `columnHeader` property in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#chartsettings).

If the column has more than one header, then need to mention all the headers separated by the delimiter **-**, for example,**Germany-Road Bikes**. Using the property `columnDelimiter` in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#chartsettings), one can set the desired delimiter to separate the column headers.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        columnHeader: "Germany-Road Bikes", columnDelimiter: "-",
        chartSeries: { type: 'Doughnut' }
    } as ChartSettings;

    public dataSourceSettings: IDataOptions = {
        columns: [{ name: 'Country' }, { name: 'Products' }],
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        drilledMembers: [{ name: 'Country', items: ['Germany'] }],
        filters: [],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        rows: [{ name: 'Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
    }

    public pivotObj: PivotViewComponent;
    render() {
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]} /></PivotViewComponent>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Label Customization

The data labels are visible by default showing header name. Its visibility can be modified using the `visible` boolean property in `dataLabel`. With regard to the label arrangement, the **Smart Labels** options help to arrange labels efficiently without overlapping. It can be disabled by setting the `enableSmartLabels` property in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#chartsettings) as "false".
The `position` property in `dataLabel` allows to specify the position of the data label. The available options are,
* `Outside`: Positions the label outside the point. It is the default option.
* `Inside`: Positions the label inside the point.

In the following code sample, the data labels are placed inside.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        enableSmartLabels: false,
        chartSeries: { dataLabel: {visible:true, position: "Inside" }, type: 'Pyramid' }
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
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]} /></PivotViewComponent>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

The **Connector Line** will be visible when the data label is placed outside the chart. It can be customized using the `connectorStyle` property in `dataLabel` for its color, length, width etc. In the following code sample, the connector line is customized.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;
    public chartSettings: ChartSettings = {
        chartSeries: {
            dataLabel: {visible:true, connectorStyle: { length: '50px', width: 2, dashArray: '5,3', color: '#f4429e' } },
            type: 'Funnel'
        }
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
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]} /></PivotViewComponent>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Pie and Doughnut Customization

User can draw pie and doughnut charts within the specified range using the `startAngle` and `endAngle` properties in [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/). The default value of the `startAngle` property is **0**, and the `endAngle` property is **360**. By customizing these properties, user can draw semi pie and semi doughnut charts.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        chartSeries: { startAngle: 270, endAngle: 90, type: 'Doughnut' }
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
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]} /></PivotViewComponent>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

Users can get doughnut chart from pie chart and vice-versa using the `innerRadius` property in [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/). If the property is greater than **0** percent, the doughnut chart will appear from the pie chart.
> It takes the value only in percentage.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: {innerRadius: "140", type: 'Pie' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>  
  }
};

ReactDOM.render(<App />,document.getElementById('pivotview'));

```

{% endtab %}

### Exploding Series Points

Exploding can be enabled by setting the `explode` property in [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/) to **true**. The series points will be exploded either on mouse click or touch.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        chartSeries: { explode: true, type: 'Pie' }
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
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]} /></PivotViewComponent>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Field List

User can enable the field list by setting the property [`showFieldList`](https://ej2.syncfusion.com/react/documentation/api/pivotview#showfieldlist) as **true**.
By using this, user can customize the report dynamically and view the result in pivot chart. For more information regarding the field list, refer the [field list](./field-list) topic.

In the following sample, the Popup mode of field list is enabled in the pivot chart.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart, FieldList } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: { type: 'Bar' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} showFieldList={true} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart, FieldList]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Grouping Bar

User can enable the grouping bar by setting the property [`showGroupingBar`](https://ej2.syncfusion.com/react/documentation/api/pivotview#showgroupingbar) as **true**. The grouping bar in pivot chart shows a dropdown list in value axis instead of buttons. The dropdown list holds list of value fields bounded in the [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings) and it can be switched to draw the pivot chart with the selected value field. This has been defined as the default behavior in the pivot chart component. For more information regarding the grouping bar, refer the [grouping bar](./grouping-bar) topic.

> For multiple axis support, buttons will be placed in value axis instead of dropdown list.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart, GroupingBar } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: { type: 'Bar' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} showGroupingBar={true} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart, GroupingBar]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

For accumulation charts alone, a drop-down list will be placed in the column axis instead of the buttons. The drop-down list shows the column headers available in the pivot table. Users can dynamically switch column headers with the help of the drop-down list, and the accumulation chart will be updated accordingly.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart, GroupingBar } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

    public displayOption: DisplayOption = {
        view: 'Chart'
    } as DisplayOption;

    public chartSettings: ChartSettings = {
        chartSeries: { type: 'Pie' }
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
        return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} showGroupingBar={true} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart, GroupingBar]} /></PivotViewComponent>
    }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Single Axis

By default, the pivot chart will be drawn with the value field (measure) which is set first in the report under value axis. But, user can change to specific value field using the property [`value`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#value) class.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: { type: 'Column' },
    value: 'Amount'
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Multi axis

User can draw the pivot chart with multiple value fields by setting the property [`enableMultiAxis`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#enablemultiaxis) in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings) as **true**. In the below code sample, the pivot chart will be drawn with both value fields "Sold" and "Amount" available in the [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings).

> The multi axis support is not applicable for the accumulation chart types like pie, doughnut, pyramid, and funnel.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    enableMultiAxis: true, chartSeries: { type: 'Column' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

If the user binds more value fields, the result will be multiple pivot charts, and each chart will shrink within the parent container height. To avoid this, set the [`enableScrollOnMultiAxis`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettings/#enablescrollonmultiaxis) property in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettings/) to **true**. By doing so, each pivot chart will only shrink to a minimal "160px" – "180px" height showing a vertical scrollbar for a clear view.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    enableScrollOnMultiAxis:true,enableMultiAxis: true, chartSeries: { type: 'Column' }
  } as ChartSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }, {name: 'Products', type: 'Count'}]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Series customization

User can customize series of the pivot chart using [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#chartseries) in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings) class. The changes handled in the property will be reflected commonly in all chart series.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
      chartSeries: { type: 'Column', enableTooltip: false, border: { color: '#000', width: 2 } }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

User can also customize the pivot chart series individually using the [`chartSeriesCreated`](../api/pivotview/pivotViewModel/#chartseriescreated) event, which occurs after the pivot chart series has been created. You can customize each series individually by iterating them.

In the following sample, the even series are hidden in the pivot chart.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart, ChartSeriesCreatedEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

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

  chartSeriesCreated(args: ChartSeriesCreatedEventArgs): void {
        for (let pos:number = 0; pos < args.series.length; pos++) {
            if (pos % 2 == 0) {
                args.series[pos].visible = false;
            }
        }
  }

  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} chartSeriesCreated={this.chartSeriesCreated}><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Axis customization

User can customize axis of the pivot chart using [`primaryXAxis`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#primaryxaxis) and [`primaryYAxis`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#primaryyaxis) properties in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings).

> Axis customization is not applicable for the accumulation chart types like pie, doughnut, pyramid, and funnel.

In the following sample, title of y-axis and x-axis are customized.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, DisplayOption, Inject, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: { type: 'Column' },
    primaryXAxis: { title: 'X axis title' },
    primaryYAxis: { title: 'Y axis title' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings}><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Legend customization

User can customize legend using [`legendSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#legendsettings) in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings). By default, legend will be visible and it can be hidden by setting the property `Visible` in [`legendSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#legendsettings) as **false**.

The pivot chart support different types of legend shapes as follows,

* Circle
* Rectangle
* VerticalLine
* Pentagon
* InvertedTriangle
* SeriesType
* Triangle
* Diamond
* Cross
* HorizontalLine

Here **seriesType** would act as the default shape and it can changed using the property [`legendShape`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotSeriesModel/#legendshape) in [`chartSeries`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#chartseries).

Also user can set the position of the legend in pivot chart using the property [`position`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotChartSettingsLegendSettings/#position) in [`legendSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/chartSettingsModel/#legendsettings). The available options to set the legend position are as follows,

* Auto: Places the legend based on area type. This is the default.
* Top: Displays the legend at the top of the pivot chart.
* Left: Displays the legend at the left of the pivot chart.
* Bottom: Displays the legend at the bottom of the pivot chart.
* Right: Displays the legend at the right of the pivot chart.
* Custom: Displays the legend based on the given x and y values.

> By default, the legend is not visible for the accumulation chart types like pie, doughnut, pyramid, and funnel.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    legendSettings: { position: 'Right' },
    chartSeries: { type: 'Column', legendShape: 'Pentagon' }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## User Interaction

### Marker and CrossHair

User can enable and customize the marker and crosshair using [`markerSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotChartSeriesMarkerSettings/) and [`crosshairSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotChartSettingsCrosshairSettings/) properties in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings) class respectively.

Also user can enable and customize the crosshair tooltip for axes using [`crosshairTooltip`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotChartAxisCrosshairTooltip/).

> Marker and crosshair is not applicable for the accumulation chart types like pie, doughnut, pyramid, and funnel.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    crosshair: { enable: true },
    chartSeries: {
        type: 'Line',
        marker: { fill: '#EEE', height: 10, width: 10, shape: 'Pentagon', visible: true }
    },
    primaryXAxis: { crosshairTooltip: { enable: true, fill: '#ff0000' } },
    primaryYAxis: { crosshairTooltip: { enable: true, fill: '#0000FF' } }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Zooming and Panning

User can customize zooming and panning option using the property [`zoomSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/) in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings).

The pivot chart support four types of zooming which can be set as follows,

* [`enablePinchZooming`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/#enablepinchzooming)
* [`enableSelectionZooming`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/#enableselectionzooming)
* [`enableDeferredZooming`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/#enabledeferredzooming)
* [`enableMouseWheelZooming`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/#enablemousewheelzooming)

and three modes of zooming direction that specifies whether to zoom vertically or horizontally or in both ways which are,

* x: Pivot chart can be zoomed horizontally.
* y: Pivot chart can be zoomed  vertically.
* x,y: Pivot chart can be zoomed both vertically and horizontally.

This can be set using the property [`mode`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/#mode) in [`zoomSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/). By default, if the pivot chart is zoomed, a toolbar would display with the options - Zoom, ZoomIn, ZoomOut, Pan, Reset. User can also customize its option using the property [`toolbarItems`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/#toolbaritems) in [`zoomSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotZoomSettings/).

> Zooming and panning is not applicable for the accumulation chart types like pie, doughnut, pyramid, and funnel.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: {
        type: 'Column'
    },
    zoomSettings: {
        enableDeferredZooming: true,
        enableMouseWheelZooming: true,
        enablePinchZooming: true,
        enableSelectionZooming: true
    }
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
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Tooltip

By default, tooltip for the pivot chart is enabled. User can customize it by using the property [`tooltipSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotTooltipSettings/) in [`chartSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#chartsettings).

> The tooltip can be disabled by setting the property [`enable`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotTooltipSettings/#enable) in [`tooltipSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview/pivotTooltipSettings/) as **false**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

  public displayOption: DisplayOption = {
    view: 'Chart'
  } as DisplayOption;

  public chartSettings: ChartSettings = {
    chartSeries: {
        type: 'Column'
    },
    tooltip: {
        enableMarker: true,
        textStyle: { color: '#000' },
        fill: '#FFF',
        opacity: 1,
        border: { color: '#000' }
    }
  } as ChartSettings;

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' },{ name: 'Products', type: 'Count'}]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Export

The pivot chart can be exported using the [`chartExport`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#chartexport) method which holds parameters like export type, file name, PDF orientation, width, and height in the same order. The mandatory parameters for this method are export type and file name whereas other parameters are optional.

The following are the four export types:

* PNG
* JPEG
* SVG
* PDF

In the following code sample, exporting can be done using an external button named as "Chart Export".

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

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

  exportClick(): void {
    this.pivotObj.chartExport('PNG', 'result');
  }
  render() {
    return <div><div><ButtonComponent cssClass='e-primary' onClick={this.exportClick.bind(this)}>Export</ButtonComponent></div><div><PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent></div></div>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Print

The rendered pivot chart can be printed directly from the browser by calling [`printChart`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#printchart) method.

In the following code sample, printing can be done using an external button named as "Print".

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { IDataOptions, IDataSet, PivotViewComponent, Inject, DisplayOption, PivotChart } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';
import { ChartSettings } from '@syncfusion/ej2-pivotview/src/pivotview/model/chartSettings';

class App extends React.Component<{}, {}>{

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
    return <div><div><ButtonComponent cssClass='e-primary' onClick={this.printClick.bind(this)}>Print</ButtonComponent></div><div><PivotViewComponent height={350} ref={d => this.pivotObj = d!} id='PivotView' chartSettings={this.chartSettings} displayOption={this.displayOption} dataSourceSettings={this.dataSourceSettings} ><Inject services={[PivotChart]}/></PivotViewComponent></div></div>
  }

  printClick(): void {
    this.pivotObj.printChart();
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}