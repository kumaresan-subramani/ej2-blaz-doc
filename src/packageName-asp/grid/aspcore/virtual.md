---
title: "Virtualization"
component: "Grid"
description: "Learn how to improve performance in the Essential JS 2 DataGrid control by using row and column virtualization and grouping with virtualization. Also learn about the limitations of virtualization."
---

# Virtualization

Grid allows you to load large amount of data without performance degradation.

## Row Virtualization

Row virtualization allows you to load and render rows only in the content viewport. It is an alternative way of paging in which the data will be loaded while scrolling vertically. To setup the row virtualization, you need to define
[`enableVirtualization`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EnableVirtualization.html) as true and content height by [`height`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Height.html) property.

The number of records displayed in the Grid is determined implicitly by height of the content area. Also, you have an option to define a visible number of records by
the [`pageSize`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridPageSettings~PageSize.html) property of [`e-grid-pagesettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PageSettings.html) tag helper. The loaded data will be cached and reused when it is needed for next time.

{% aspTab template="grid/virtual-grid/row-virtualization", sourceFiles="row-virtualization.cs" %}

{% endaspTab %}

## Column Virtualization

Column virtualization allows you to virtualize columns. It will render columns which are in the viewport. You can scroll horizontally to view more columns.

To setup the column virtualization, set the
[`enableVirtualization`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EnableVirtualization.html) and
[`enableColumnVirtualization`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EnableColumnVirtualization.html) properties as **true**.

{% aspTab template="grid/virtual-grid/column-virtualization", sourceFiles="Column-virtualization.cs" %}

{% endaspTab %}

> Column's [`width`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Width.html) is required for column virtualization. If column's width is not defined then Grid will consider its value as **200px**.

## Virtualization with Grouping

Both the row and column virtualization can be used along with grouping. At initial rendering, the virtual height of scrollbar will be set based on the total number of records and after grouping, it will be refreshed based on the grouped state(expand/collapse). While collapse the group caption row in current viewport then the next view page grouped records are shown.

> The collapsed/expanded state will persist only for local dataSource while scrolling.

## Limitations for Virtualization

* While using column virtualization, column width should be in the pixel. Percentage values are not accepted.
* Due to the element height limitation in browsers, the maximum number of records loaded by the grid is limited by the browser capability.
* Cell selection will not be persisted in both row and column virtualization.
* Virtual scrolling is not compatible with batch editing, detail template and hierarchy features.
* Group expand and collapse state will not be persisted.
* Since data is virtualized in grid, the aggregated information and total group items are displayed based on the current view items. To get these information regardless of the view items, refer to the
[`Group with Page`](./grouping/#group-with-paging) topic.
* The page size provided must be two times larger than the number of visible rows in the grid. If the page size is failed to meet this condition then the size will be determined by grid.
* The height of the grid content is calculated using the row height and total number of records in the data source and hence features which changes row height such as text wrapping are not supported. If you want to increase the row height to accommodate the content then you can specify the row height as below to ensure all the table rows are in same height.

```css
.e-grid .e-row {
    height: 2em;
}
```

* Programmatic selection using the **selectRows** method is not supported in virtual scrolling.