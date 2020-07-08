---
title: "Grouping"
component: "Grid"
description: "Learn how to group rows, apply initial groups, customize caption templates, and group by format in the Essential JS 2 DataGrid control."
---

# Grouping

The Grid has options to group records by dragging and dropping the column header to the group drop area. When grouping is applied, grid records are organized into a hierarchical structure to facilitate easier expansion and collapse of records.

To enable grouping in the grid, set the [`allowGrouping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowGrouping.html) as true. Grouping options can be configured through the [`e-grid-groupsettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~GroupSettings.html)  tag helper.

{% aspTab template="grid/grouping/group", sourceFiles="group.cs" %}

{% endaspTab %}

> * You can group and ungroup columns by using the **groupColumn** and
**ungroupColumn** methods.
> * To disable grouping for a particular column, set the
[`allowGrouping`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowGrouping.html) to false in **e-grid-column** tag helper.

## Initial group

To apply group at initial rendering, set the column field name in the [`columns`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridGroupSettings~Columns.html) property of **e-grid-groupsettings** tag helper.

{% aspTab template="grid/grouping/initial-group", sourceFiles="initial-group.cs" %}

{% endaspTab %}

## Caption template

You can customize the group caption by using the [`captionTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridGroupSettings~CaptionTemplate.html) property of **e-grid-groupsettings** tag helper.

{% aspTab template="grid/grouping/caption-temp", sourceFiles="caption-temp.cs" %}

{% endaspTab %}

## Hide drop area

To avoid ungrouping or further grouping of a column after initial column
grouping, define the [`showDropArea`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridGroupSettings~ShowDropArea.html) of **e-grid-groupsettings**  as false.

{% aspTab template="grid/grouping/hide-drop-area", sourceFiles="hide-drop-area.cs" %}

{% endaspTab %}

## Group with paging

On grouping columns with paging feature, the aggregated information and total items are displayed based on the current page. The grid does not consider aggregated information and total items from other pages. To get additional details (aggregated information and total items) from other pages, set the [`disablePageWiseAggregates`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridGroupSettings~DisablePageWiseAggregates.html) property of **e-grid-groupsettings** to false.

> If remote data is bound to grid dataSource, two requests will be sent when performing grouping action; one for getting the grouped data and another for getting aggregate details and total items count.

## Group by format

By default, a column will be grouped by the data or value present for the particular row. To group the numeric
or datetime column based on the mentioned format, you have to enable the
[`enableGroupByFormat`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~EnableGroupByFormat.html) property of the corresponding
grid columns.

{% aspTab template="grid/grouping/group-format", sourceFiles="group-format.cs" %}

{% endaspTab %}

## Grouping events

During the group action, the grid component triggers two events. The [`actionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionBegin.html) event
triggers before the group action starts and the [`actionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionComplete.html) event triggers after the group action is completed. Using these events you can perform any action.

{% aspTab template="grid/grouping/grouping-events", sourceFiles="grouping-events.cs" %}

{% endaspTab %}

> The `args.requestType` is based on the current action name. For example, when grouping, the `args.requestType` value will be 'grouping'.

## Collapse by external button

You can collapse the selected group from an external button by invoking the **expandCollapseRows** method.

{% aspTab template="grid/grouping/collapse", sourceFiles="collapse.cs" %}

{% endaspTab %}

## Reordering on Grouped Columns

Grid provides an option to interchange the position of the Grouped Columns by dragging and dropping the grouped headercells in the droparea. So, any new column entering into the droparea can also be dropped in any position.

To enable this feature, you have to set the [`allowReordering`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridGroupSettings~AllowReordering.html) of **e-grid-groupsettings** property as **true**.

{% aspTab template="grid/grouping/reordering", sourceFiles="GroupOrdering.cs" %}

{% endaspTab %}

## See Also

* [Exporting grouped records](./excel-exporting#Exporting-grouped-records)