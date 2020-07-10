---
title: "Sorting"
component: "Pivot Table"
description: "Sorting allows user to order the field headers either in ascending or descending."
---

# Sorting

## Member Sorting

Allows to order field members in rows and columns either in ascending or descending order. By default, field members in rows and columns are in ascending order.

Member sorting can be enabled by setting the [`enableSorting`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~EnableSorting.html) property in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag to **true**. After enabling this API, click the sort icon besides each field in row or column axis, available in field list or grouping bar UI for re-arranging members either in ascending or descending order.

> By default the [`enableSorting`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~EnableSorting.html) property in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag set as **true**. If we set it as **false**, then the field members arrange in pivot table as its data source order. And, the sort icons in grouping bar and field list buttons will be removed.

![output](images/sorting_fl.png "Member sorting icon in field list")
<br/>
![output](images/sorting_gb.png "Member sorting icon in grouping bar")
<br/>
![output](images/sorting_grid.png "Resultant pivot table on member sort")

Member sorting can also be configured using the [`e-sortsettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewSortSetting_members.html) tag through code behind, during initial rendering. The settings required to sort are:

* [`name`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewSortSetting~Name.html): It allows to set the field name.
* [`order`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewSortSetting~Order.html): It allows to set the sort direction either to ascending or descending of the respective field.

> By default the [`order`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewSortSetting~Order.html) property in the [`e-sortsettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewSortSetting_members.html) tag set as [**Ascending**](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Sorting.html). Meanwhile, we can arrange the field members as its order in data source by setting it as [**None**](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Sorting.html) where the sort icons in grouping bar and field list buttons for the corresponding field will be removed.

{% aspTab template="pivot-table/sorting", sourceFiles="Sorting.cs" %}

{% endaspTab %}

## Value sorting

> This property is applicable only for relational data source.

Allows to sort individual value field and its aggregated values either in row or column axis in both ascending and descending order. It can been enabled by setting the [`enableValueSorting`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~EnableValueSorting.html) property in [`ejs-pivotview`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) tag to **true**. On enabling, end user can sort the values by directly clicking the value field header positioned either in row or column axis of the pivot table component.

The value sorting can also be configured using the [`e-valuesortsettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewValueSortSettings_members.html) option through code behind. The settings required to sort value fields are:

* [`headerText`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewValueSortSettings~HeaderText.html): It allows to set the header names with delimiters, that is used for value sorting. The header names are arranged from Level 1 to Level N, down the hierarchy with a delimiter for better specification.
* [`headerDelimiter`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewValueSortSettings~HeaderDelimiter.html): It allows to set the delimiters string to separate the header text between levels.
* [`sortOrder`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewValueSortSettings~SortOrder.html): It allows to set the sort direction of the value field.

{% aspTab template="pivot-table/value-sorting", sourceFiles="ValueSorting.cs" %}

{% endaspTab %}

![output](images/valuesorting.png)