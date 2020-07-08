---
title: "Aggregates"
component: "Grid"
description: "Learn how to aggregate rows, apply custom aggregates, and format the aggregate values in the Essential JS 2 DataGrid control."
---

# Aggregates

Aggregate values are displayed in the footer, group footer, or group caption of the Grid. It can be configured through [`e-grid-aggregates`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Aggregates.html) tag helper.
 [`field`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Field.html) and
  [`type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Type.html)
 are the minimum properties required to represent an aggregate column.

By default, the aggregate value can be displayed in the footer, group, and caption cells. To show the aggregate value in one of the cells, use the [`footerTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~FooterTemplate.html),
[`groupFooterTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~GroupFooterTemplate.html),
 or [`groupCaptionTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~GroupCaptionTemplate.html) property.

## Built-in aggregate types

The aggregate type should be specified in the [`type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Type.html) property to configure an aggregate column.

The built-in aggregates are,
* Sum
* Average
* Min
* Max
* Count
* TrueCount
* FalseCount

> * Multiple aggregates can be used for an aggregate column by setting the [`type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Type.html) property
with an array of aggregate types.
> * Multiple types for a column is supported only when one of the aggregate templates is used.

## Footer aggregate

Footer aggregate value is calculated for all the rows, and it is displayed in the footer cells. Use the [`footerTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~FooterTemplate.html) property to render the aggregate value in footer cells.

{% aspTab template="grid/aggregate/footer-agg", sourceFiles="footer-agg.cs" %}

{% endaspTab %}

> The aggregate values must be accessed inside the template using their corresponding [`type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Type.html) name.

## How to format aggregate value

You can format the aggregate value result by using the [`format`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Format.html) property.

{% aspTab template="grid/aggregate/format-agg", sourceFiles="format-agg.cs" %}

{% endaspTab %}

## Group and caption aggregate

Group and caption aggregate values are calculated from the current group items.
If [`groupFooterTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~GroupFooterTemplate.html) is provided, the aggregate values are displayed in the group footer cells; and if [`groupCaptionTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~GroupCaptionTemplate.html)
 is provided, aggregate values are displayed in the group caption cells.

{% aspTab template="grid/aggregate/group-caption", sourceFiles="group-caption.cs" %}

{% endaspTab %}

> The aggregate values must be accessed inside the template using their corresponding [`type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Type.html) name.

## Custom aggregate

To calculate the aggregate value with your own aggregate functions, use the custom aggregate option. To use custom aggregation, specify the [`type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~Type.html) as `Custom`, and provide the custom aggregate function in the [`customAggregate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~CustomAggregate.html) property in [`e-grid-aggregates`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Aggregates.html) tag helper.

The custom aggregate function will be invoked with different arguments for total and group aggregations.
* **Total aggregation**: The custom aggregate function will be called with the whole data and current [`aggregateColumn`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~ColumnName.html)
object.
* **Group aggregation**: This will be called with the current group details and [`aggregateColumn`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridAggregateColumn~ColumnName.html) object.

{% aspTab template="grid/aggregate/custom-agg", sourceFiles="custom-agg.cs" %}

{% endaspTab %}

> To access the custom aggregate value inside the template, use the key as **Custom**.

## Reactive aggregate update

When using batch editing, the aggregate values will be refreshed on every cell save. The footer, group footer, and group caption aggregate values will be refreshed.

> Adding a new record to the grouped grid will not refresh the aggregate values.

{% aspTab template="grid/aggregate/reactive-agg-batch-edit", sourceFiles="reactive-agg-batch-edit.cs" %}

{% endaspTab %}

### Refresh aggregates in inline edit mode

By default, reactive aggregate update is not supported by inline and dialog edit modes as it is not feasible to anticipate the value change event for every editor. But, you can refresh the aggregates manually in the inline edit mode using the refresh method of aggregate module.

In the following code, the input event for the Freight column editor has been registered and the aggregate value has been refreshed manually.

{% aspTab template="grid/aggregate/reactive-agg-inline-edit", sourceFiles="reactive-agg-inline-edit.cs" %}

{% endaspTab %}