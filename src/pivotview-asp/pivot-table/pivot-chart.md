---
title: "Pivot Chart"
component: "Pivot Table"
description: "It allows the user to display a chart component based on the pivot report bound on it. And the UI of the chart component can be customized."
---

# Pivot Chart

In pivot table component, pivot chart would act as an additional visualization component with its basic and important characteristic like drill down and drill up, 15+ chart types, series customization, axis customization, legend customization, export, print and tooltip. Its main purpose is to show the pivot data in graphical format.

If user prefers, the pivot chart component can also be displayed individually with pivot values and can change the report dynamically with the help of field list and grouping bar. Using the [`PivotViewDisplayOption`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDisplayOption_members.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) class, user can set the visibility of grid and chart in pivot table component. It holds below properties,

* [`View`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDisplayOption~View.html): Specifies the pivot table component to display grid alone or chart alone or both.
* [`Primary`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDisplayOption~Primary.html): Specifies the pivot table to display either grid or chart as primary component during initial loading. It is applicable only when setting the property [`View`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDisplayOption~View.html) to [**View.Both**](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.View.html).

The below sample displays the pivot chart component based on the pivot report bound on it.

{% aspTab template="pivot-table/pivot-chart/display-view", sourceFiles="DisplayView.cs" %}

{% endaspTab %}

## Data Binding

End user can bind both local and remote data binding options available in the component to feed the data. The [`DataSource`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~DataSource.html) property can be assigned either with an instance of `DataManager` or list of object.
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

[**ChartSeriesType.Line**](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.ChartSeriesType.html) is the default pivot chart type. User can change the pivot chart type by using the property [`Type`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSeries~Type.html) in [`PivotChartSeries`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSeries_members.html) class.

In the below code sample, the pivot chart type is set as [**ChartSeriesType.Bar**](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.ChartSeriesType.html).

{% aspTab template="pivot-table/pivot-chart/chart-type", sourceFiles="ChartType.cs" %}

{% endaspTab %}

![output](images/charttype.png)

## Field List

User can enable the field list by setting the property [`ShowFieldList`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~ShowFieldList.html) in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) class as **true**.
By using this, user can customize the report dynamically and view the result in pivot chart. For more information regarding the field list, refer the [field list](./field-list) topic.

In the following sample, the `Popup` mode of field list is enabled in the pivot chart integration.

{% aspTab template="pivot-table/pivot-chart/chart-fieldlist", sourceFiles="ChartFieldList.cs" %}

{% endaspTab %}

![output](images/pivotchart-FL.png)

## Grouping Bar

User can enable the grouping bar by setting the property [`ShowGroupingBar`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~ShowGroupingBar.html) in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) class as **true**. The grouping bar in pivot chart shows a dropdown list in value axis instead of buttons. The dropdown list holds list of value fields bounded in the [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) and it can be switched to draw the pivot chart with the selected value field. This has been defined as the default behavior in the pivot chart component. For more information regarding the grouping bar, refer the [grouping bar](./grouping-bar) topic.

> For multiple axis support, buttons will be placed in value axis instead of dropdown list.

{% aspTab template="pivot-table/pivot-chart/chart-groupingbar", sourceFiles="ChartGroupingBar.cs" %}

{% endaspTab %}

![output](images/pivotchart-gbar.png)

## Single Axis

By default, the pivot chart will be drawn with the value field (measure) which is set first in the report under value axis. But, user can change to specific value field using the property [`Value`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings~Value.html) in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class.

{% aspTab template="pivot-table/pivot-chart/chart-groupingbar", sourceFiles="ChartGroupingBar.cs" %}

{% endaspTab %}

![output](images/chart_single_axis.png)

## Multi Axis

User can draw the pivot chart with multiple value fields by setting the property [`EnableMultiAxis`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings~EnableMultiAxis.html) in [`PivotChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class as **true**. In the below code sample, the pivot chart will be drawn with both value fields "Sold" and "Amount" available in the [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html).

{% aspTab template="pivot-table/pivot-chart/chart-multivalue", sourceFiles="ChartMultiValue.cs" %}

{% endaspTab %}

![output](images/multi-axis.png)

## Series Customization

User can customize series of the pivot chart using [`ChartSeries`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSeries_members.html) in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class. The changes handled in the property will be reflected commonly in all chart series.

In the following sample, the pivot chart type and border has been changed for all the series.

{% aspTab template="pivot-table/pivot-chart/chartseries", sourceFiles="ChartSeries.cs" %}

{% endaspTab %}

![output](images/chart-series.png)

User can also customize the pivot chart series individually using the `ChartSeriesCreated` event, which occurs after the pivot chart series has been created. You can customize each series individually by iterating them.

In the following sample, the even series are hidden in the pivot chart.

{% aspTab template="pivot-table/pivot-chart/chartseries-event", sourceFiles="ChartSeriesEvent.cs" %}

{% endaspTab %}

![output](images/chart-series-event.png)

## Axis Customization

User can customize axis of the pivot chart using [`PrimaryXAxis`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings~PrimaryXAxis.html) and [`PrimaryYAxis`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings~PrimaryYAxis.html) properties in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class.

{% aspTab template="pivot-table/pivot-chart/chart-axis", sourceFiles="ChartAxis.cs" %}

{% endaspTab %}

![output](images/axis-customization.png)

## Legend Customization

User can customize legend using [`LegendSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSettingsLegendSettings_members.html) in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class. By default, legend will be visible and it can be hidden by setting the property [`Visible`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSettingsLegendSettings~Visible.html) in [`LegendSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSettingsLegendSettings_members.html) class as **false**.

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

Here **SeriesType** would act as the default shape and it can changed using the property [`LegendShape`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSeries~LegendShape.html) in [`ChartSeries`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSeries_members.html) class.

Also user can set the position of the legend in pivot chart using the property [`Position`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSettingsLegendSettings~Position.html) in [`LegendSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSettingsLegendSettings_members.html) class. The available options to set the legend position are as follows,

* Auto: Places the legend based on area type. This is the default.
* Top: Displays the legend at the top of the pivot chart.
* Left: Displays the legend at the left of the pivot chart.
* Bottom: Displays the legend at the bottom of the pivot chart.
* Right: Displays the legend at the right of the pivot chart.
* Custom: Displays the legend based on the given x and y values.

In the following sample, the legend shape and its position can be customized.

{% aspTab template="pivot-table/pivot-chart/legend", sourceFiles="Legend.cs" %}

{% endaspTab %}

![output](images/legend-settings.png)

## User Interaction

### Marker and CrossHair

User can enable and customize the marker and crosshair using [`MarkerSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSeriesMarkerSettings_members.html) and [`CrosshairSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotChartSettingsCrosshairSettings_members.html) properties in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class respectively.

Also user can enable and customize the crosshair tooltip for axes using [`PrimaryXAxis`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings~PrimaryXAxis.html) and [`PrimaryYAxis`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings~PrimaryYAxis.html) classes.

{% aspTab template="pivot-table/pivot-chart/marker", sourceFiles="Marker.cs" %}

{% endaspTab %}

![output](images/marker-crosshair.png)

### Zooming and Panning

User can customize zooming and panning option using the property [`ChartZoomSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings_members.html) in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class.

The pivot chart support four types of zooming which can be set as follows,

* [`EnablePinchZooming`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings~EnablePinchZooming.html)
* [`EnableSelectionZooming`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings~EnableSelectionZooming.html)
* [`EnableDeferredZooming`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings~EnableDeferredZooming.html)
* [`EnableMouseWheelZooming`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings~EnableMouseWheelZooming.html)

and three modes of zooming direction that specifies whether to zoom vertically or horizontally or in both ways which are,

* x: Pivot chart can be zoomed horizontally.
* y: Pivot chart can be zoomed  vertically.
* x,y: Pivot chart can be zoomed both vertically and horizontally.

This can be set using the property [`Mode`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings~Mode.html) in [`ZoomSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings_members.html) class. By default, if the pivot chart is zoomed, a toolbar would display with the options - Zoom, ZoomIn, ZoomOut, Pan, Reset. User can also customize its option using the property [`ToolbarItems`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings~ToolbarItems.html) in [`ZoomSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotZoomSettings_members.html) class.

{% aspTab template="pivot-table/pivot-chart/zooming", sourceFiles="Zooming.cs" %}

{% endaspTab %}

![output](images/zooming.png)

### Tooltip

By default, tooltip for the pivot chart is enabled. User can customize it by using the property [`TooltipSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotTooltipSettings_members.html) in [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html) class.

> The tooltip can be disabled by setting the property [`Enable`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotTooltipSettings~Enable.html) in [`TooltipSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotTooltipSettings_members.html) class as **false**.

{% aspTab template="pivot-table/pivot-chart/chart-tooltip", sourceFiles="ChartTooltip.cs" %}

{% endaspTab %}

![output](images/tooltip.png)

## Export

The pivot chart can be exported using the `chartExport` method which holds parameters like export type, file name, PDF orientation, width, and height in the same order. The mandatory parameters for this method are export type and file name whereas other parameters are optional.

The following are the four export types:

* PNG
* JPEG
* SVG
* PDF

In the following code sample, exporting can be done using an external button named as "Chart Export".

{% aspTab template="pivot-table/pivot-chart/export", sourceFiles="Export.cs" %}

{% endaspTab %}

![output](images/chart-export.png)

## Print

The rendered pivot chart can be printed directly from the browser by calling `printChart` method.

In the following code sample, printing can be done using an external button named as "Print".

{% aspTab template="pivot-table/pivot-chart/print", sourceFiles="Print.cs" %}

{% endaspTab %}

![output](images/print-chart.png)