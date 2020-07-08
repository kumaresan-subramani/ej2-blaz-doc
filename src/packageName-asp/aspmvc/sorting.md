---
title: "Sorting"
component: "Grid"
description: "Learn how to sort rows in the Essential JS 2 DataGrid control, perform initial sorting, multi-column sorting and customize sorting logic."
---

# Sorting

Sorting enables you to sort data in the **Ascending** or **Descending** order.
To sort a column, click the column header.

To enable sorting in the Grid, set the [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowSorting.html) to true. Sorting options can be configured through the [`SortSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSortSettings.html).

{% aspTab template="grid/sorting/sorting", sourceFiles="sorting.cs" %}

{% endaspTab %}

> Grid columns are sorted in the **Ascending** order. If you click the already sorted column, the sort direction toggles.
> You can apply and clear sorting by invoking **sortColumn** and **clearSorting** methods.
> To disable sorting for a particular column, set the [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~AllowSorting.html) property of [`Column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) to false.

## Initial sort

To sort at initial rendering, set the **Field** and
**Direction** in [`Columns`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSortSettings~Columns.html) property of [`SortSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSortSettings.html).

{% aspTab template="grid/sorting/initial-sort", sourceFiles="initial-sort.cs" %}

{% endaspTab %}

## Multi-column sorting

You can sort more than one column in a Grid. To sort multiple columns, press and hold the **CTRL** key and click the column header. The sorting order will be displayed in the header while performing multi-column sorting.

To clear sorting for a particular column, press the "Shift + mouse left click".

> The [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowSorting.html) must be **true** while enabling multi-column sort.
> Set [`AllowMultiSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowMultiSorting.html) property as **false** to disable multi-column sorting.

{% aspTab template="grid/sorting/multi-column-sort", sourceFiles="multi-column-sort.cs" %}

{% endaspTab %}

## Sort order

By default, the sorting order will be as **ascending -> descending -> none**.

When first click a column header it sorts the column in ascending. Again click the same column header, it will sort the column in descending. A repetitive third click on the same column header will clear the sorting.

## Sort foreign key column based on Text

For local data in Grid, sorting will be performed based on the [`ForeignKeyValue`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~ForeignKeyValue.html) property of [`Column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html).

For remote data in Grid, sorting will be performed based on the [`ForeignKeyField`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~ForeignKeyField.html) instead of [`ForeignKeyValue`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~ForeignKeyValue.html). To sort a column based on the displayed text and not based on the [`ForeignKeyField`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~ForeignKeyField.html), we need to handle the sorting operation at the server side.

The following code example describes the handling of sorting operation at the server side.

{% aspTab template="grid/sorting/foreign-sort", sourceFiles="foreign-sort.cs" %}

{% endaspTab %}

## Sorting events

During the sort action, the grid component triggers two events. The [`ActionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionBegin.html) event triggers before the sort action starts, and the [`ActionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionComplete.html) event triggers after the sort action is completed. Using these events you can perform the needed actions.

{% aspTab template="grid/sorting/sort-event", sourceFiles="sort-event.cs" %}

{% endaspTab %}

> The **args.requestType** is the current action name. For example, in sorting the **args.requestType** is sorting.

## Touch interaction

When you tap the grid header on touchscreen devices, the selected column header is sorted. A popup ![sorting](./images/sorting.jpg) is displayed for multi-column sorting. To sort multiple columns, tap the popup![msorting](./images/msorting.jpg), and then tap the desired grid headers.

> The [`AllowMultiSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowMultiSorting.html) and [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowSorting.html) should be **true** then only the popup will be shown.

The following screenshot shows grid touch sorting.

![Touch interaction](./images/touch-sorting.jpg)
