---
title: "Show or Hide columns in Dialog editing"
component: "Grid"
description: "Learn how to Show or Hide columns in Dialog editing."
---

# Show or Hide columns in Dialog editing

You can show hidden columns or hide visible column's editor in the dialog while editing the grid record using [`actionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionBegin.html) and [`actionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionComplete.html) events.

In the [`actionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionBegin.html) event, based on **requestType** as **beginEdit** or  **add**. We can show or hide the editor by using [`visible`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Visible.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) tag helper.

In the [`actionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionComplete.html) event, based on **requestType** as **save**. We can reset the properties back to the column state.

In the below example, we have rendered the grid columns **CustomerID** as hidden column and **ShipCountry** as visible column. In the edit mode, we have changed the **CustomerID** column to visible state and **ShipCountry** column to hidden state.

{% aspTab template="grid/edit/show-hide-edit-dialog", sourceFiles="*.cs" %}

{% endaspTab %}
