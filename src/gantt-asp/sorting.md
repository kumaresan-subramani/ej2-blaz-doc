---
title: "Sorting"
component: "Gantt"
description: "Learn how to order the records in the Essential JS 2 Gantt control."
---

# Sorting

Sorting enables you to sort data in the ascending or descending order. To sort a column, click the column header.

To sort multiple columns, press and hold the CTRL key and click the column header. You can clear sorting of any one of the multi-sorted columns by pressing and holding the SHIFT key and clicking the specific column header.

To enable sorting in the Gantt control, set the [`AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~AllowSorting.html) property to true. Sorting options can be configured through the [`SortSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~SortSettings.html) property.

{% aspTab template="gantt/sorting/enableSorting", sourceFiles="enableSorting.cs" %}

{% endaspTab %}

The following screenshot shows the output of multicolumn sorting in Gantt control.

![Alt text](images/multiSorting.png)

> * Gantt columns are sorted in the ascending order. If you click the already sorted column, the sort direction toggles.
> * To disable sorting for a particular column, set the [`Columns.AllowSorting`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttColumn~AllowSorting.html) property to false.

## Sorting column on Gantt initialization

The Gantt control can be rendered with sorted columns initially, and this can be achieved by using the [`SortSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~SortSettings.html) property. You can add columns that are sorted initially in the [`SortSettings.Columns`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.GanttSortSettings~Columns.html) collection defined with `Field` and `Direction` properties. The following code example shows how to add the sorted column to Gantt initialization.

{% aspTab template="gantt/sorting/initialSort", sourceFiles="initialSort.cs" %}

{% endaspTab %}

## Sorting column dynamically

Columns in the Gantt control can be sorted dynamically using the `sortColumn` method. The following code example demonstrates how to invoke the `sortColumn` method by clicking the custom button.

{% aspTab template="gantt/sorting/dynamicSort", sourceFiles="dynamicSort.cs" %}

{% endaspTab %}

![Alt text](images/beforeSorting.png)

Before Sorting

![Alt text](images/afterSorting.png)

After Sorting

## Clear all the sorted columns dynamically

In the Gantt control, you can clear all the sorted columns and return to previous position using the `clearSorting` public method. The following code snippet shows how to clear all the sorted columns by clicking the custom button.

{% aspTab template="gantt/sorting/clearSorting", sourceFiles="clearSorting.cs" %}

{% endaspTab %}

## Sorting events

During the sort action, the Gantt control triggers two events. The [`ActionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~ActionBegin.html) event triggers before the sort action starts, and the [`ActionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Gantt.Gantt~ActionComplete.html) event triggers after the sort action is completed.

{% aspTab template="gantt/sorting/eventHandlers", sourceFiles="eventHandlers.cs" %}

{% endaspTab %}

> The `args.requestType` is the current action name. For example, for sorting the `args.requestType`, value is **sorting**.