---
title: "Selection"
component: "Grid"
description: "Learn how to select rows and cells, use range selection, and use check box selection in the Essential JS 2 DataGrid control."
---

# Selection

Selection provides an option to highlight a row or a cell. It can be done through simple mouse down or arrow keys. To disable selection in the Grid, set the [`AllowSelection`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridBuilder~AllowSelection.html) to false.

The grid supports two types of selection that can be set by using the [`SelectionSettings.Type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~Type.html). They are:

* **`Single`**: The `Single` value is set by default, and it only allows selection of a single row or a cell.
* **`Multiple`**: Allows you to select multiple rows or cells.
To perform the multi-selection, press and hold CTRL key and click the desired rows or cells. To select range of rows or cells, press and hold the SHIFT key and click the rows or cells.

{% aspTab template="grid/selection/selection", sourceFiles="selection.cs" %}

{% endaspTab %}

## Selection mode

The grid supports three types of selection mode that can be set by using
the [`SelectionSettings.Mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~Mode.html). They are:

* **`Row`**: The `Row` value is set by default, and allows you to select only rows.
* **`Cell`**: Allows you to select only cells.
* **`Both`**: Allows you to select rows and cells at the same time.

{% aspTab template="grid/selection/selection-mode", sourceFiles="selection-mode.cs" %}

{% endaspTab %}

## Cell selection

Cell selection can be done through simple mouse down or arrow keys (up, down, left, and right).

The grid supports two types of cell selection mode that can be set by using
the [`SelectionSettings.CellSelectionMode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~CellSelectionMode.html). They are:

* **`Flow`**: The `Flow` value is set by default. The range of cells are selected between the start index and end index that includes in between cells of rows.
* **`Box`**: Range of cells are selected from the start and end column indexes that includes in between cells of rows within the range.

{% aspTab template="grid/selection/cell-selection", sourceFiles="cell-selection.cs" %}

{% endaspTab %}

> Cell selection requires the [`SelectionSettings.Mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~Mode.html) to be `Cell` or  `Both`, and
`Type` should be `Multiple`.

## Checkbox selection

Checkbox selection provides an option to select multiple grid records with help of checkbox in each row.

To render the checkbox in each grid row, you need to use checkbox column with type as `checkbox` using the  column [`Type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumnBuilder~Type.html) property.

{% aspTab template="grid/selection/checkbox", sourceFiles="checkbox.cs" %}

{% endaspTab %}

> By default, selection is allowed by clicking a grid row or checkbox in that row. To allow selection only through checkbox, you can set the
[`SelectionSettings.CheckboxOnly`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~CheckboxOnly.html) property to true.
> Selection can be persisted in all the operations using the [`SelectionSettings.PersistSelection`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~PersistSelection.html) property.
For persisting selection on the grid, any one of the columns should be defined as a primary key using the [`Columns.IsPrimaryKey`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~IsPrimaryKey.html) property.

### Checkbox selection Mode

In checkbox selection, selection can also be done by clicking on rows. This selection provides two types of Checkbox Selection mode which can be set by using the following API,
`selectionSettings.checkboxMode`. The modes are;

* **`Default`**: This is the default value of the checkboxMode. In this mode, user can select multiple rows by clicking rows one by one.
* **`ResetOnRowClick`**: In ResetOnRowClick mode, when user clicks on a row it will reset previously selected row. Also you can perform multiple-selection in this mode by press
and hold CTRL key and click the desired rows. To select range of rows, press and hold the SHIFT key and click the rows.

{% aspTab template="grid/selection/windowslikeselection", sourceFiles="windows.cs" %}

{% endaspTab %}

## Toggle selection

The Toggle selection allows to perform selection and unselection of the particular row or cell. To enable toggle selection, set [`enableToggle`](./api-selectionSettings.html#enableToggle-boolean) property of the selectionSettings as true. If you click on the selected row or cell then it will be unselected and vice versa.

{% aspTab template="grid/selection/toggleselection", sourceFiles="toggleselection.cs" %}

{% endaspTab %}

> If multi selection is enabled, then first click on any selected row (without pressing Ctrl key), it will clear the multi selection and in second click on the same row, it will be unselected.

## Select row at Initial rendering

To select a row at initial rendering, set the [`SelectedRowIndex`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridBuilder~SelectedRowIndex.html) value.

{% aspTab template="grid/selection/select-row", sourceFiles="select-row.cs" %}

{% endaspTab %}

## Get selected row indexes

You can get the selected row indexes by using the `getSelectedRowIndexes` method.

{% aspTab template="grid/selection/selected-row-index", sourceFiles="selected-row-index.cs" %}

{% endaspTab %}

## Touch interaction

When you tap a grid row on touchscreen device, the tapped row is selected.
It also shows a popup ![selection](./images/selection.jpg)  for multi-row selection.
To select multiple rows or cells, tap the popup![mselection](./images/mselection.jpg)  and then tap the desired rows or cells.

> Multi-selection requires the selection `Type` to be `Multiple`.

The following screenshot represents a grid touch selection in the device.

![Touch interaction](./images/touch-selection.jpg)

## Multiple Selection based on condition

You can select multiple grid rows based on condition by using the [`selectRows`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~Type.html) method.

In the following code, the rows which contains `ShipCountry` value as `Brazil` are selected at initial rendering.

{% aspTab template="grid/selection/conditional-selection", sourceFiles="conditional-selection.cs" %}

{% endaspTab %}

## Simple Multiple Row selection

You can select multiple rows by clicking on rows one by one. This will not deselect the previously selected rows. To deselect the previously selected row, you can click on the  selected row. You can enable this behavior by using `selectionSettings.enableSimpleMultiRowSelection` property.

{% aspTab template="grid/selection/simplemultiselect", sourceFiles="multiselection.cs" %}

{% endaspTab %}