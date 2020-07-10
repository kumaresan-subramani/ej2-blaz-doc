---
title: "Editing"
component: "Pivot Table"
description: "Editing allows to perform CRUD operation in the raw items of any cells of the pivot table."
---

# Editing

> This feature is applicable only for relational data source.

Cell edit allows to add, delete, or update the raw items of any value cell from the pivot table. The raw items can be viewed in a data grid inside a new window on double-clicking the appropriate value cell. In the data grid, CRUD operations can be performed by double-clicking the cells or using toolbar options. Once user finishes editing raw items, aggregation will be performed for the updated values in pivot table component immediately. This support can be enabled by setting the [`AllowEditing`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings~AllowEditing.html) property in [`PivotViewCellEditSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings_members.html) class to **true**.

The CRUD operations available in the data grid toolbar and command column are:

| Toolbar Button | Actions |
|----------------|---------|
| Add | Add a new row.|
| Edit | Edit the current row or cell.|
| Delete | Delete the current row.|
| Update | Update the edited row or cell.|
| Cancel | Cancel the edited state. |

The following are the supported edit types in the data grid:

* Normal
* Dialog
* Batch
* Command Columns

## Normal

In normal edit mode, when user starts editing, the state of the currently selected row alone will be completely changed to edit state. User can change the cell values and save it to the data source by clicking "Update" toolbar button. To enable the normal edit, set the [`Mode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings~Mode.html) property in [`PivotViewCellEditSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings_members.html) class to [**EditMode.Normal**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.EditMode.html).

> The normal edit mode is the default mode of editing..

{% aspTab template="pivot-table/editing/normal", sourceFiles="Normal.cs" %}

{% endaspTab %}

![output](images/edit-normal.png)

## Dialog

In dialog edit mode, when you start editing, the currently selected row data will be shown in a dialog.
You can change the cell values and save it to the data source by clicking **Save**.
To enable the dialog edit, set the [`Mode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings~Mode.html) property in [`PivotViewCellEditSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings_members.html) class to [**EditMode.Dialog**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.EditMode.html).

{% aspTab template="pivot-table/editing/dialog", sourceFiles="Dialog.cs" %}

{% endaspTab %}

![output](images/edit-dialog.png)

## Batch

In batch edit mode, when you double-click the table cell, the state of target cell is changed to edit state.
You can perform bulk save (added, changed, and deleted data in the single request) to the data source by clicking the toolbar's **Update** button.

To enable the batch edit, set the [`Mode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings~Mode.html) property in [`PivotViewCellEditSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings_members.html) class to [**EditMode.Batch**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.EditMode.html).

{% aspTab template="pivot-table/editing/batch", sourceFiles="Batch.cs" %}

{% endaspTab %}

![output](images/edit-batch.png)

## Command column

An additional column appended in the grid layout holds the command buttons to perform the CRUD operation.
To enable the command columns, set the [`AllowCommandColumns`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings~Mode.html) property in [`PivotViewCellEditSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewCellEditSettings_members.html) class to **true**.

The available built-in command buttons are:

| Command Button | Actions |
|----------------|---------|
| Edit | Edit the current row.|
| Delete | Delete the current row.|
| Save | Update the edited row.|
| Cancel | Cancel the edited state. |

{% aspTab template="pivot-table/editing/cc", sourceFiles="CC.cs" %}

{% endaspTab %}

![output](images/edit-command.png)

## Editing using the pivot chart

Users can also add, delete, or update the underlying raw items of any data point via pivot chart. The raw items will be shown in the data grid in the new window by clicking the appropriate data point. Then you can edit the raw items as mentioned above by any of the edit types (normal, dialog, batch and command column).

{% aspTab template="pivot-table/editing/chart", sourceFiles="Chart.cs" %}

{% endaspTab %}

![output](images/drillthrough-chart-before.png)
<br/>
<br/>
![output](images/editing-dialog.png)

## Events

### DrillThrough

For more information [`refer`](./drill-through/#drillthrough) here.

### BeginDrillThrough

For more information [`refer`](./drill-through/#begindrillthrough) here.