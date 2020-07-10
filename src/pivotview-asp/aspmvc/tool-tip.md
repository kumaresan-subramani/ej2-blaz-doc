---
title: "Tooltip"
component: "Pivot Table"
description: "Describes about enabling and disabling tooltip in pivot table"
---

# Tooltip

The tooltip can be enabled or disabled by setting the [`showTooltip`](https://ej2.syncfusion.com/react/documentation/api/pivotview/#showtooltip) property to **true**. By default, tooltip is enabled in the pivot table.

{% aspTab template="pivot-table/pivot-tooltip", sourceFiles="ToolTip.cs" %}

{% endaspTab %}

{% aspTab template="pivot-table/toolbar/toolbar-customize", sourceFiles="ToolbarCustomize.cs" %}

{% endaspTab %}

## Tooltip Template

User can design their own tooltip by setting the property [`TooltipTemplate`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~TooltipTemplate.html) with own HTML elements. The property accepts both HTML string and ID attribute. The following place holders are available to display its dynamic values inside the HTML elements.

`${rowHeaders}` – Row headers of the selected value cell.

`${columnHeaders}`  – Column headers of the selected value cell.

`${rowFields}` – Row fields of the selected value cell.

`${columnFields}` – Column fields of the selected value cell.

`${valueField}` – Field name of the selected value cell.

`${aggregateType}` – Aggregate type of the selected value cell.

`${value}` - Formatted value of the selected value cell.

The tooltip customization is common for both pivot table and pivot chart or it can be done individually as well. To customize the pivot table tooltip, the above procedure needs to be followed. To customize the pivot chart tooltip alone use `Template` property of tooltip under [`ChartSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewChartSettings_members.html).

In the below sample, the pivot table and pivot chart shows customized tooltip layouts.

{% aspTab template="pivot-table/tooltip-template", sourceFiles="tooltip-template.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD012 -->
![output](images/tooltipTemplate.png)
<br/>
<br/>
<br/>
![output](images/tooltipTemplate-chart.png)