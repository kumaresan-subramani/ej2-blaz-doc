---
title: "Pivot Chart"
component: "Pivot Table"
description: "It allows users to display a pivot chart control based on the pivot report bound on it and customizes the UI of the pivot chart control."
---

# Pivot Chart

You can enable the pivot chart and visualize it against pivot data as a graphical format in pivot table itself. The pivot chart control can be displayed individually for pivot values, and you can change the report dynamically using the field list and grouping bar. More than 15 types of pivot charts are available. This document explains available features and settings of the pivot chart control.

To display the pivot chart control, set the [`displayOption.view`](../api/pivotview/displayOption/#view) property to pivot chart.

>You should inject the `PivotChart` module to make the pivot chart features available in the pivot table.

The following sample displays the pivot chart control based on the pivot report bound on it.

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

You can bind both the local and remote data binding options in the control to feed data. The [`dataSource`](../api/pivotview/dataSource/#data) property can be assigned either with the instance of `DataManager` or JavaScript object array collection.
For more information, refer to the topic [Data Binding](./data-binding).

## Pivot Chart settings

You can customize the pivot chart visualization by using the [`chartSettings`](../api/pivotview/chartSettings) property.

By default, the pivot chart can be drawn with the pivot data populated by the first value from value axis. But, you can draw the pivot chart by the desired value field by setting the [`value`](../api/pivotview/chartSettings/#value) property to value field name in the data source.

### Multiple axis

You can draw the pivot chart with multiple value fields available in the data source by setting the [`enableMultiAxis`](../api/pivotview/chartSettings/#enablemultiaxis) property to true.

In the following sample, the pivot chart will be drawn with both the **Sold** and **Amount** value fields available in the data source.

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

### Series customization

You can customize the series of pivot chart using the [`chartSeries`](../api/pivotview/chartSettings/#chartseries) property. The changes in the property can be reflected commonly in all the pivot chart series.

In the following sample, the pivot chart type and border has been changed for all the series.

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

### Axis customization

You can customize the axis of the pivot chart by using the [`primaryXAxis`](../api/pivotview/chartSettings/#primaryxaxis) and [`primaryYAxis`](../api/pivotview/chartSettings/#primaryyaxis) properties.

In the following sample, title of y-axis and x-axis are customized.

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

## Pivot Chart types

It supports 19 different types of pivot charts as follows:

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

**Line** is the default pivot chart type. You can change the pivot chart type by using the [`type`](../api/pivotview/pivotSeriesModel/#type) property.

In the following sample, the pivot chart type is set to bar.

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

## Legend customization

You can customize the legend by using the [`legendSettings`](../api/pivotview/chartSettings/#legendsettings) property. By default, the legend can be visible. You can hide it by using the `legendSettings.visible` property.

It supports different types of legend shapes as follows:

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

The default legend is SeriesType. It draws the shape based on pivot chart type. You can change the legend shape by using the [`chartSeries.legendShape`](../api/pivotview/pivotSeriesModel/#legendshape) property.

You can set the position of legend in the pivot chart using the `legendSettings.position` property.

The following are the available options to set the legend position:

* Auto: Places the legend based on area type. This is the default.
* Top: Displays the legend at the top of the pivot chart.
* Left: Displays the legend at the left of the pivot chart.
* Bottom: Displays the legend at the bottom of the pivot chart.
* Right: Displays the legend at the right of the pivot chart.
* Custom: Displays the legend based on the given x and y values.

In the following sample, the legend shape and its position can be customized.

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

## User interaction

### Marker and crosshair

You can enable and customize the marker and crosshair using the [`marker`](../api/pivotview/pivotSeriesModel/#marker) and [`crosshair`](../api/pivotview/chartSettings/#crosshair) properties, respectively.

You can enable and customize the crosshair tooltip for axes using the [`crosshairTooltip`](../api/pivotview/pivotAxisModel/#crosshairtooltip) property.

In the following sample, the marker and crosshair can be enabled and customized.

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

### Zooming and panning

You can customize the zooming and panning options using the [`zoomSettings`](../api/pivotview/chartSettings/#zoomsettings) property.

It supports four types of zooming, which can be set as follows:

* [`enablePinchZooming`](../api/pivotview/pivotZoomSettingsModel/#enablepinchzooming)
* [`enableSelectionZooming`](../api/pivotview/pivotZoomSettingsModel/#enableselectionzooming)
* [`enableDeferredZooming`](../api/pivotview/pivotZoomSettingsModel/#enabledeferredzooming)
* [`enableMouseWheelZooming`](../api/pivotview/pivotZoomSettingsModel/#enablemousewheelzooming)

The following are the three types of modes for zooming the pivot chart:

* x: Pivot Chart can be zoomed horizontally.
* y: Pivot Chart can be zoomed  vertically.
* x,y: Pivot Chart can be zoomed in both vertically and horizontally.

The zooming mode can be set using the [`mode`](../api/pivotview/pivotZoomSettingsModel/#mode) property.

By default, if the pivot chart is zoomed, a toolbar displays options such as Zoom, ZoomIn, ZoomOut, Pan, and Reset. You can set the desired option by using the `toolbarItems` property.

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

By default, the tooltip is enabled. You can customize it by using the [`tooltip`](../api/pivotview/chartSettings/#tooltip) property.

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

## Grouping bar

You can enable the grouping bar by setting the `showGroupingBar` property to true. In the grouping bar of pivot chart integration, the drop-down list is placed in value axis instead of buttons. The drop-down list holds the list of value fields bound in data source and it can be switched to draw the pivot chart with the selected value field.

> For the multiple axis support, the buttons will be placed in value axis instead of drop-down list.

For more information, refer to the topic [Grouping Bar](./grouping-bar).

In the following sample, the grouping bar is enabled in the pivot chart integration.

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
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Field list

You can enable both `Fixed` and `Popup` modes of field list options in the pivot chart integration. So, you can customize the report dynamically and view the result in pivot chart.
For more information, refer to the topic [Field List](./field-list).

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

## Export and print

The pivot chart can be exported using the `chartExport` method which holds the parameters export type, file name, PDF orientation, width, and height.

The following are the four types of exporting options:

* PNG
* JPEG
* SVG
* PDF

You can print the pivot chart using the `printChart` method.

In the following sample, exporting and printing can be triggered by the **Export** and **Print** external buttons, respectively.

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

let exportBtn: Button = new Button({ isPrimary: true }, '#chartexport');
let printBtn: Button = new Button({ isPrimary: true }, '#chartprint');

document.getElementById('chartexport').addEventListener('click', () => {
    pivotTableObj.chartExport('PNG', 'result');
});
document.getElementById('chartprint').addEventListener('click', () => {
    pivotTableObj.printChart();
});

```

{% endtab %}