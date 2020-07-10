---
title: "Row and Column"
component: "Pivot Table"
description: "Miscellaneous aspects of customizing the pivot table."
---

<!-- markdownlint-disable MD012 -->

# Row and Column

## Width and Height

Allows end user to set the pivot table's height and width by using [`Height`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Height.html) and [`Width`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Width.html) properties in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) class respectively. The supported formats to set [`Height`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Height.html) and [`Width`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Width.html) properties are,

* Pixel: For example - 100, 200, "100px", "200px".
* Percentage: For example - "100%", "200%".
* Auto: It is applicable for [`Height`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Height.html) property alone in-order to render the pivot table beyond its parent container height without vertical scrollbar. The parent container here would show its vertical scrollbar as soon as the component reaches beyond its dimension.

> The pivot table will not be displayed less than **400px**, since it's the minimum width of the component.

{% aspTab template="pivot-table/grid-customization/size", sourceFiles="Size.cs" %}

{% endaspTab %}

![output](images/height-width.png)

## Row Height

Allows end user to set the height of each pivot table rows commonly using the [`RowHeight`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~RowHeight.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class.

> By default, the [`RowHeight`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~RowHeight.html) property is set as **36** pixels for desktop layout and **48** pixels for mobile layout.
> The height of the column headers alone may vary when grouping bar feature is enabled.

In the below code sample, the [`RowHeight`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~RowHeight.html) property is set as **60** pixels.


{% aspTab template="pivot-table/grid-customization/row-height", sourceFiles="RowHeight.cs" %}

{% endaspTab %}

![output](images/row-height.png)

## Column Width

Allows end user to set the width of each pivot table columns commonly using the [`ColumnWidth`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~ColumnWidth.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class.

> By default, the [`ColumnWidth`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~ColumnWidth.html) property is set as **110** pixels to each columns except the first column. For first column, **250** pixels and **200** pixels are set respectively with and without grouping bar.

In the below example, the [`ColumnWidth`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~ColumnWidth.html) property is set as **200** pixels.

{% aspTab template="pivot-table/grid-customization/column-width", sourceFiles="ColumnWidth.cs" %}

{% endaspTab %}

![output](images/column-width.png)

## Reorder

Allows end user to reorder a particular column header from one index to another index within the pivot table through drag-and-drop option. It can be enabled by setting the [`AllowReordering`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~AllowReordering.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class to **true**.

{% aspTab template="pivot-table/grid-customization/re-order", sourceFiles="ReOrder.cs" %}

{% endaspTab %}

![output](images/reorder.png)

## Column Resizing

Allows end user to resize the columns by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. To enable column resizing option, set the [`AllowResizing`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~AllowResizing.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class to **true**.

> By default, the column resizing option is enabled.
> In RTL mode, user can click and drag the left edge of the header cell to resize the column.

{% aspTab template="pivot-table/grid-customization/column-resizing", sourceFiles="ColumnResizing.cs" %}

{% endaspTab %}

![output](images/resize.png)

## Text Wrap

Allows end user to wrap the cell content to the next line when it exceeds the boundary of the cell width. To enable text wrap, set the [`AllowTextWrap`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~AllowTextWrap.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class to **true**.

{% aspTab template="pivot-table/grid-customization/text-wrap", sourceFiles="TextWrap.cs" %}

{% endaspTab %}

![output](images/textwrap.png)

## Grid Lines

Allows end user to display cell border for each cells using [`GridLines`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~GridLines.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class.

Available mode of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

> By default, pivot table renders grid lines in **Both** mode.

{% aspTab template="pivot-table/grid-customization/grid-lines", sourceFiles="GridLines.cs" %}

{% endaspTab %}

![output](images/gridlines.png)

## Selection

Selection provides an option to highlight a row or a column or a cell. It can be done through simple mouse down or arrow keys. To enable selection in the pivot table, set the [`AllowSelection`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~AllowSelection.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class to **true**.

The pivot table supports two types of selection that can be set using [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings~Type.html) property in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings_members.html) class. The selection types are:

* `Single`: It is set by default, and it only allows selection of a single row or a column or a cell.
* `Multiple`: Allows you to select multiple rows or columns or cells.
To perform multi-selection, press and hold "CTRL" key and click the desired rows or cells. To select range of rows or cells, press and hold the "SHIFT" key and click the rows or columns or cells.

{% aspTab template="pivot-table/grid-customization/selection", sourceFiles="Selection.cs" %}

{% endaspTab %}

![output](images/selection.png)

### Selection Mode

The pivot table supports four types of selection mode that can be set using [`Mode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings~Mode.html) property in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings_members.html) class.. The selection modes are:

* [**SelectionMode.Row**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.SelectionMode.html): It is set by default, and allows user to select only rows.
* [**SelectionMode.Column**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.SelectionMode.html): Allows user to select only columns.
* [**SelectionMode.Cell**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.SelectionMode.html): Allows user to select only cells.
* [**SelectionMode.Both**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.SelectionMode.html): Allows user to select rows and columns at the same time.

{% aspTab template="pivot-table/grid-customization/selection-mode", sourceFiles="SelectionMode.cs" %}

{% endaspTab %}

![output](images/selection2.png)

### Cell Selection Mode

The pivot table supports two types of cell selection mode that can be set using [`CellSelectionMode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings~CellSelectionMode.html) in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings_members.html) class. The cell selection modes are:

* [**PivotCellSelectionMode.Flow**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotCellSelectionMode.html): It is set by default. The range of cells are selected between the start index and end index that includes in-between cells of rows.
* [**PivotCellSelectionMode.Box**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotCellSelectionMode.html): Range of cells are selected from the start and end column indexes that includes in-between cells of rows within the range.

{% aspTab template="pivot-table/grid-customization/cell-selection", sourceFiles="CellSelection.cs" %}

{% endaspTab %}

> Cell selection requires [`Mode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings~Mode.html) property in [`PivotViewSelectionSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings_members.html) class to be [**SelectionMode.Cell**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.SelectionMode.html) or [**SelectionMode.Both**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.SelectionMode.html), and [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewPivotSelectionSettings~Type.html) property should be `Multiple`.

![output](images/cell-selection.png)

### Changing background color of the selected cell

The background-color of the selected cell can be changed using built-in CSS names. To do so, please refer to the code sample below, which shows that the selected cells are changed to a **green yellow** color.

{% aspTab template="pivot-table/grid-customization/cell-selection-color", sourceFiles="CellSelection.cs" %}

{% endaspTab %}

![output](images/cell-selection-color.png)

### Event

#### CellSelected

The event `CellSelected` is triggered when cell selection gets completed. It provides selected cells information with its corresponding column and row headers. It has following parameters - `selectedCellsInfo`, `currentCell` and `target`. This event allows user to view selected cells information and user can pass those selected cells information to any external component for data binding.

{% aspTab template="pivot-table/grid-customization/cell-event", sourceFiles="CellSelection.cs" %}

{% endaspTab %}

![output](images/cellselected_event.png)

#### CellSelecting

The event `CellSelecting` triggers before cell gets selected gets completed. It provides selected cells information with its corresponding column and row headers. It has following parameters - `currentCell`, `data` and `cancel`.

{% aspTab template="pivot-table/grid-customization/cell-selecting-event", sourceFiles="CellSelection.cs" %}

{% endaspTab %}

## Clip Mode

The clip mode provides options to display its overflow cell content in the pivot table. It can be configured using the [`ClipMode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~ClipMode.html) property in [`PivotViewGridSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings_members.html) class. The pivot table supports three types of clip modes which are:

* `Clip`: Truncates the cell content when it overflows its area.
* `Ellipsis`: Displays ellipsis when the cell content overflows its area.
* `EllipsisWithTooltip`: Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

>By default, [`ClipMode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewGridSettings~ClipMode.html) value is set to `Ellipsis`.

{% aspTab template="pivot-table/grid-customization/clip-mode", sourceFiles="ClipMode.cs" %}

{% endaspTab %}

![output](images/clipmode.png)


## Cell Template

User can customize the pivot table cell element by using the `CellTemplate` property in `PivotViewTemplates` class. The `CellTemplate` property accepts either an HTML string or the element's ID, which can be used to append additional HTML elements to showcase each cell with custom format.

In this demo, the revenue cost for each year is represented with trend icons.

{% aspTab template="pivot-table/grid-customization/cell-template", sourceFiles="cell-template.cs" %}

{% endaspTab %}

![output](images/cell_template.png)

## Events

### QueryCellInfo

The event `queryCellInfo` triggers while rendering each row and value cells in the pivot table. It allows the user to customize the current cell like adding or removing styles, editing value, etc. It has the following parameters:

* `cell` - It holds the current cell information.
* `data` - It holds the entire row data besides the current cell.
* `column` - It holds the entire column data besides the current cell.
* `pivotview` - It holds pivot table instance.

{% aspTab template="pivot-table/grid-customization/querycell", sourceFiles="QueryCell.cs" %}

{% endaspTab %}

### HeaderCellInfo

The event `headerCellInfo` triggers while rendering each column header cell in the pivot table. It allows the user to customize the element of the current header cell like adding or removing styles, editing value, etc. It has the following parameters:

* `node` - It holds the current header cell information.

{% aspTab template="pivot-table/grid-customization/headercell", sourceFiles="HeaderCell.cs" %}

{% endaspTab %}

### CellClick

The event `CellClick` triggers while clicking a cell in the pivot table. For instance, using this event end-user can either add or remove styles, edit value and also perform any other DOM manipulations. It has the following parameters:

* `currentCell` - It holds the current cell information.
* `data` - It holds the clicked cell's data like axis, formatted text, actual text, row header, column header and value informations.

{% aspTab template="pivot-table/grid-customization/cell-click", sourceFiles="CellClick.cs" %}

{% endaspTab %}


## See Also

* [Show/hide tooltip](./how-to/show-hide-tool-tip)
* [Perform cell selection and get selected cells information](./how-to/perform-cell-selection-and-get-selected-cells-information)