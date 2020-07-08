---
title: "Paging"
component: "Grid"
description: "Learn how to add and customize the pager in the Essential JS 2 DataGrid control."
---

# Paging

Paging provides an option to display Grid data in page segments. To enable paging, set the [`AllowPaging`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridBuilder~AllowPaging.html) to true. When paging is enabled, pager component renders at the bottom of the grid.
Paging options can be configured through the [`PageSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridBuilder~PageSettings.html).

In the below sample, `pageSize` is calculated based on the grid height by using the `load` event.

{% aspTab template="grid/paging/page", sourceFiles="page.cs" %}

{% endaspTab %}

> You can achieve better performance by using grid paging to fetch only a pre-defined number of records from the data source.

## Template

You can use custom elements inside the pager instead of default elements.
The custom elements can be defined by using the `Template` property.
Inside this template, you can access the `CurrentPage`, `PageSize`, `TotalPage` and `TotalRecordCount` values.

{% aspTab template="grid/paging/page-temp", sourceFiles="page-temp.cs" %}

{% endaspTab %}

## Pager with Page Size Dropdown

The pager Dropdown allows you to change the number of records in the Grid dynamically. It can be enabled by defining the `pageSettings.pageSizes` property as true.

{% aspTab template="grid/paging/pagerdropdown", sourceFiles="pagerdropdown.cs" %}

{% endaspTab %}

## How to render Pager at the Top of the Grid

By default, Pager will be rendered at the bottom of the Grid. You can also render the Pager at the top of the Grid by using the `dataBound` event.

{% aspTab template="grid/paging/pagerattop", sourceFiles="pagerattop.cs" %}

{% endaspTab %}

> During the paging action, the pager component triggers the below three events.
> * The `created` event triggers when Pager is created.
> * The `click` event triggers when the numeric items in the pager is clicked.
> * The `dropDownChanged` event triggers when pageSize DropDownList value is selected.

## See Also

* [Group with Paging](./grouping##group-with-paging)
