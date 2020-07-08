---
title: "Row"
component: "Grid"
description: "Documentation for row templates (custom row content), detail templates, and DataGrid row styles."
---

# Row

The row represents record details fetched from data source.

## Row template

The [`RowTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowTemplate.html) has an option to customise the look and behavior of the grid rows. The [`RowTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowTemplate.html) property accepts either
the template string or HTML element ID.

{% aspTab template="grid/row/row-template", sourceFiles="row-template.cs" %}

{% endaspTab %}

> The [`RowTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowTemplate.html) property accepts only the TR element.

## Detail template

The detail template provides additional information about a particular row by expanding or collapsing detail content. The [`DetailTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DetailTemplate.html) property accepts either
the template string or HTML element ID.

{% aspTab template="grid/row/detail-temp", sourceFiles="detail-temp.cs" %}

{% endaspTab %}

### Rendering custom component

To render the custom component inside the detail row, define the template in the [`DetailTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DetailTemplate.html) and render the
component in the [`DetailDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DetailDataBound.html) event.

For example, to render grid inside the detail row, place an HTML div element as the [`DetailTemplate`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DetailTemplate.html) and render the DIV element as grid component in the [`DetailDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DetailDataBound.html) event.

{% aspTab template="grid/row/custom-component", sourceFiles="custom-component.cs" %}

{% endaspTab %}

### Expand by external button

By default, detail rows render in collapsed state. You can expand a detail row by invoking the **expand** method using the external button.

{% aspTab template="grid/row/expand-external", sourceFiles="expand-external.cs" %}

{% endaspTab %}

> You can expand all the rows by using **expandAll** method.
> If you want to expand all the rows at initial Grid rendering, then use **expandAll** method in [`DataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~DataBound.html) event of the Grid.

## Drag and drop

The grid row drag and drop allows you to drag and drop grid rows to another grid or custom component. To enable row drag and drop, set the [`AllowRowDragAndDrop`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowRowDragAndDrop.html) to true.
The target component where the grid rows are to be dropped can be set by using
the **TargetID**.

{% aspTab template="grid/row/drag-drop", sourceFiles="drag-drop.cs" %}

{% endaspTab %}

> Selection feature must be enabled for row drag and drop.
> Multiple rows can be selected by clicking and dragging inside the grid.
For multiple row selection, the [`Type`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings~Type.html) property of [`SelectionSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridSelectionSettings.html) must be set to **Multiple**.

## Drag and drop within Grid

The grid row drag and drop allows you to drag and drop grid rows on the same grid using drag icon. To enable row drag and drop, set the [`AllowRowDragAndDrop`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~AllowRowDragAndDrop.html) to true.

{% aspTab template="grid/row/drag-drop-same-grid", sourceFiles="drag-drop-same-grid.cs" %}

{% endaspTab %}

## Customize rows

You can customize the appearance of a row by using the [`RowDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowDataBound.html) event.
The [`RowDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowDataBound.html) event triggers for every row. In the event handler, you can get the **RowDataBoundEventArgs** that contains details of the row.

{% aspTab template="grid/row/custom-rows", sourceFiles="custom-rows.cs" %}

{% endaspTab %}

## Styling alternate rows

You can change the grid's alternative rows' background color by overriding the **.e-altrow** class.

```css
.e-grid .e-altrow {
    background-color: #fafafa;
}
```

Please refer to the following example.

{% aspTab template="grid/row/style-alt-row", sourceFiles="style-alt-row.cs" %}

{% endaspTab %}

## Row height

You can customize the row height of grid rows through the [`RowHeight`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowHeight.html) property. The [`RowHeight`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowHeight.html) property
is used to change the row height of entire grid rows.

In the below example, the [`RowHeight`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowHeight.html) is set as 60px.

{% aspTab template="grid/row/row-height", sourceFiles="row-height.cs" %}

{% endaspTab %}

### Customize row height for particular row

Grid row height for particular row can be customized using the [`RowDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowDataBound.html)
event by setting the [`RowHeight`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowHeight.html) in arguments for each row based on the requirement.

In the below example, the row height for the row with OrderID as '10249' is set as '90px' using the [`RowDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowDataBound.html) event.

{% aspTab template="grid/row/rowheight-particular", sourceFiles="rowheight-particular.cs" %}

{% endaspTab %}

> In virtual scrolling mode, it is not applicable to set the [`RowHeight`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowDataBound.html) using the [`RowDataBound`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~RowDataBound.html) event.
