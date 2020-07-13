---
title: "Pivot Chart"
component: "Pivot Table"
description: "It allows users to display a pivot chart control based on the pivot report bound on it and customizes the UI of the pivot chart control."
---

# Pivot Chart

In pivot table component, pivot chart would act as an additional visualization component with its basic and important characteristic like drill down and drill up, 15+ chart types, series customization, axis customization, legend customization, export, print and tooltip. Its main purpose is to show the pivot data in graphical format.

If user prefers, the pivot chart component can also be displayed individually with pivot values and can change the report dynamically with the help of field list and grouping bar. Using the `displayOption` property in pivot table, user can set the visibility of grid and chart in pivot table component. It holds below properties,

* `view`: Specifies the pivot table component to display grid alone or chart alone or both.
* `primary`: Specifies the pivot table to display either grid or chart as primary component during initial loading. It is applicable only when setting the property View to `view.Both`.

The below sample displays the pivot chart component based on the pivot report bound on it.

{% tab template="pivot-table/pivot-table", es5Template="display-view", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { chartSeries: { type: 'Column' } },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Data binding

End user can bind both local and remote data binding options available in the component to feed the data. The [`dataSource`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettingsModel/#datasource) property can be assigned either with an instance of `DataManager` or  JavaScript object array collection.
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

**Line** is the default pivot chart type. User can change the pivot chart type by using the property [`type`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSeriesModel/#type) in [`chartSeries`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSeriesModel/).

In the below code sample, the pivot chart type is set as **Bar**.

{% tab template="pivot-table/pivot-table", es5Template="chart-type", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { chartSeries: { type: 'Bar' } },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Field List

User can enable the field list by setting the property [`showFieldList`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#showfieldlist) in pivot table as **true**.By using this, user can customize the report dynamically and view the result in pivot chart. For more information regarding the field list, refer the [field list](./field-list) topic.

In the following sample, the `Popup` mode of field list is enabled in the pivot chart integration.

{% tab template="pivot-table/pivot-table", es5Template="chart-fieldlist", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart, FieldList,);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { chartSeries: { type: 'Column' }},
    showFieldList: true,
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Grouping Bar

User can enable the grouping bar by setting the property [`showGroupingBar`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#showgroupingbar) in pivot table to **true**. The grouping bar in pivot chart shows a dropdown list in value axis instead of buttons. The dropdown list holds list of value fields bounded in the [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettingsModel/) and it can be switched to draw the pivot chart with the selected value field. This has been defined as the default behavior in the pivot chart component. For more information regarding the grouping bar, refer the [grouping bar](./grouping-bar) topic.

> For multiple axis support, buttons will be placed in value axis instead of dropdown list.

{% tab template="pivot-table/pivot-table", es5Template="chart-groupingbar", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart, GroupingBar } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart, GroupingBar);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { chartSeries: { type: 'Column' }},
    showGroupingBar: true,
    height: 240
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Single Axis

By default, the pivot chart will be drawn with the value field (measure) which is set first in the report under value axis. But, user can change to specific value field using the property [`value`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/#value) in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/).

{% tab template="pivot-table/pivot-table", es5Template="chart-single", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { enableMultiAxis: true, chartSeries: { type: 'Column' } },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Multi Axis

User can draw the pivot chart with multiple value fields by setting the property [`enableMultiAxis`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/#enablemultiaxis) in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/) to **true**. In the below code sample, the pivot chart will be drawn with both value fields "Sold" and "Amount" available in the [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettingsModel/).

{% tab template="pivot-table/pivot-table", es5Template="chart-multivalue", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { enableMultiAxis: true, chartSeries: { type: 'Column' } },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Series Customization

User can customize series of the pivot chart using [`chartSeries`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSeriesModel/) in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/). The changes handled in the property will be reflected commonly in all chart series.

{% tab template="pivot-table/pivot-table", es5Template="chartseries", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { chartSeries: { type: 'Column', enableTooltip: false, border: { color: '#000', width: 2 } } },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

You can also customize the pivot chart series individually using the [`chartSeriesCreated`](../api/pivotview/pivotViewModel/#chartseriescreated) event, which occurs after the pivot chart series has been created. You can customize each series individually by iterating them.

In the following sample, the even series are hidden in the pivot chart.

{% tab template="pivot-table/pivot-table", es5Template="chartseries-event", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart, ChartSeriesCreatedEventArgs } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: { chartSeries: { type: 'Column' } },
    chartSeriesCreated: (args: ChartSeriesCreatedEventArgs) => {
        for (let pos:number = 0; pos < args.series.length; pos++) {
            if (pos % 2 == 0) {
                args.series[pos].visible = false;
            }
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Axis Customization

User can customize axis of the pivot chart using [`primaryXAxis`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotAxisModel/) and [`primaryYAxis`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotAxisModel/) properties in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/).

{% tab template="pivot-table/pivot-table", es5Template="chart-axis", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart, ChartSeriesCreatedEventArgs } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
        chartSeries: { type: 'Column' },
        primaryXAxis: { title: 'X axis title' },
        primaryYAxis: { title: 'Y axis title' }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Legend Customization

User can customize legend using [`legendSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSettingsLegendSettings/) in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettingsModel/). By default, legend will be visible and it can be hidden by setting the property [`visible`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSettingsLegendSettings/#visible) in [`legendSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSettingsLegendSettings/) to **false**.

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

Here **SeriesType** would act as the default shape and it can changed using the property [`legendShape`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSeriesModel/#legendshape) in [`chartSeries`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotSeriesModel/).

Also user can set the position of the legend in pivot chart using the property [`position`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSettingsLegendSettings/#position) in [`legendSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSettingsLegendSettings/). The available options to set the legend position are as follows,

* Auto: Places the legend based on area type. This is the default.
* Top: Displays the legend at the top of the pivot chart.
* Left: Displays the legend at the left of the pivot chart.
* Bottom: Displays the legend at the bottom of the pivot chart.
* Right: Displays the legend at the right of the pivot chart.
* Custom: Displays the legend based on the given x and y values.

{% tab template="pivot-table/pivot-table", es5Template="legend", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
        legendSettings: { position: 'Right' },
        chartSeries: { type: 'Column', legendShape: 'Pentagon' }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## User Interaction

### Marker and CrossHair

User can enable and customize the marker and crosshair using [`markerSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSeriesMarkerSettings/) and [`crosshairSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartSettingsCrosshairSettings/) properties in [`chartSettings`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.PivotChartSettings.html) respectively.

Also user can enable and customize the crosshair tooltip for axes using [`crosshairTooltip`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotChartAxisCrosshairTooltip/) in primary X and Y axes

{% tab template="pivot-table/pivot-table", es5Template="marker", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
        crosshair: { enable: true },
        chartSeries: {
         type: 'Line',
         marker: { fill: '#EEE', height: 10, width: 10, shape: 'Pentagon', visible: true }
        },
        primaryXAxis: { crosshairTooltip: { enable: true, fill: '#ff0000' } },
        primaryYAxis: { crosshairTooltip: { enable: true, fill: '#0000FF' } }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Zooming and Panning

User can customize zooming and panning option using the property [`zoomSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/) in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettings/).

The pivot chart support four types of zooming which can be set as follows,

* [`EnablePinchZooming`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/#enablepinchzooming)
* [`EnableSelectionZooming`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/#enableselectionzooming)
* [`EnableDeferredZooming`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/#enabledeferredzooming)
* [`EnableMouseWheelZooming`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/#enablemousewheelzooming)

and three modes of zooming direction that specifies whether to zoom vertically or horizontally or in both ways which are,

* x: Pivot chart can be zoomed horizontally.
* y: Pivot chart can be zoomed  vertically.
* x,y: Pivot chart can be zoomed both vertically and horizontally.

This can be set using the property [`mode`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/#mode) in [`zoomSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/). By default, if the pivot chart is zoomed, a toolbar would display with the options - Zoom, ZoomIn, ZoomOut, Pan, Reset. User can also customize its option using the property [`toolbarItems`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/#toolbaritems) in [`zoomSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotZoomSettingsModel/).

In the following sample, all the four types of zooming are enabled with toolbar options.

{% tab template="pivot-table/pivot-table", es5Template="zooming", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
        chartSeries: {
            type: 'Column'
        },
        zoomSettings: {
            enableDeferredZooming: true,
            enableMouseWheelZooming: true,
            enablePinchZooming: true,
            enableSelectionZooming: true
        }
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Tooltip

By default, tooltip for the pivot chart is enabled. User can customize it by using the property [`tooltip`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotTooltipSettingsModel/) in [`chartSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/chartSettings/).

> The tooltip can be disabled by setting the property [`enable`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotTooltipSettingsModel/) in [`tooltip`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/pivotTooltipSettingsModel/) as **false**.

In the following sample, the default appearance of tooltip can be modified.

{% tab template="pivot-table/pivot-table", es5Template="chart-tooltip", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
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
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Export

The pivot chart can be exported using the `chartExport` method which holds parameters like export type, file name, PDF orientation, width, and height in the same order. The mandatory parameters for this method are export type and file name whereas other parameters are optional.

The following are the four export types:

* PNG
* JPEG
* SVG
* PDF

In the following code sample, exporting can be done using an external button named as "Export".

{% tab template="pivot-table/chart-export", es5Template="export", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
        chartSeries: {
         type: 'Column'
        }
    },
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let exportBtn: Button = new Button({ isPrimary: true });
exportBtn.appendTo('#chartexport');

document.getElementById('chartexport').addEventListener('click', () => {
    pivotTableObj.chartExport('PNG', 'result');
});


```

{% endtab %}

## Print

The rendered pivot chart can be printed directly from the browser by calling [`PrintChart`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.EjsPivotView%601~PrintChart.html) method.

In the following code sample, printing can be done using an external button named as "Print".

{% tab template="pivot-table/chart-print", es5Template="print", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, PivotChart } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(PivotChart);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    displayOption: { view: 'Chart' },
    chartSettings: {
        chartSeries: {
         type: 'Column'
        }
    },
    height: 320
});
pivotTableObj.appendTo('#PivotTable');

let printBtn: Button = new Button({ isPrimary: true });
printBtn.appendTo('#chartprint');

document.getElementById('chartprint').addEventListener('click', () => {
    pivotTableObj.printChart();
});

```

{% endtab %}