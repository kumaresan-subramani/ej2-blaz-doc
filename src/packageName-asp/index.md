---
title: "Overview"
component: "Grid"
description: "Documentation on the rich features of the Essential JS 2 DataGrid (DataTable) control, including built-in support for editing, filtering, grouping, paging, sorting, and exporting to Excel."
---

# Overview

The Grid component is used to display and manipulate tabular data with configuration options to control the way the data is presented. It can pull data from data sources such as array of JavaScript objects, `OData web services`, or `DataManager` and binding data fields to columns. It also displays the column header to identify the field with support for grouped records.

The most important features available in the grid component are paging, sorting, filtering, searching, and grouping.

## Key Features

* [**Data sources**](./data-binding.html): Binds the grid component with an array of JavaScript objects or DataManager.
* [**Sorting**](./sorting.html) and [**grouping**](./grouping.html): Supports **n** level of sorting and grouping.
* [**Filtering**](./filtering.html): Offers filter bar in each column to filter data.
* [**Paging**](./paging.html): Allows easy switching between pages using the pager bar.
* [**Editing**](./edit.html):provides the options for create, read, update, and delete operations.
* [**Columns**](./columns.html):The column definitions are used as the dataSource schema in the Grid. This plays a vital role in rendering column values in the required format.
    * [**Reordering**](./columns.html#reorder): Allows drag and drop of any column anywhere in the grid’s column header row, thus allowing repositioning of columns.
    * [**Column Chooser**](./columns.html#column-chooser):The column chooser provides a list of column names paired with check boxes that allow the visibility to be toggled on the fly.
    * [**Resizing**](./columns.html#column-resizing):Resizing allows changing column width on the fly by simply dragging the right corner of the column header.
    * [**Freeze**](./scrolling.html#frozen-rows-and-columns):Columns and rows can be frozen to allow scrolling and comparing cell values.
    * [**Cell Spanning**](./columns.html#column-spanning):Grid cells can be spanned based on the preferred criteria.
    * [**Foreign data source**](./columns.html#foreign-key-column):This provides the option to show values from external or lookup data sources in a column based on foreign key/value mapping.
    * [**Cell Styling**](./how-to.html#customize-column-styles):Grid cell styles can be customized either by using CSS or programmatically.
* [**Selection**](./selection.html):Rows or cells can be selected in the grid. One or more rows or cells can also be selected by holding Ctrl or Command, or programmatically.
* [**Templates**](./columns.html#column-template) - Templates can be used to create custom user experiences in the grid.
* [**Aggregation**](./aggregates.html) - Provides the option to easily visualized the Aggregates for column values.
* [**Context menu**](./context-menu.html) -The context menu provides a list of actions to be performed in the grid. It appears when a cell, header, or the pager is right-clicked.
* [**Clipboard**](./clipboard.html) - Selected rows and cells can be copied from the grid
* [**Export**](./pdf-export.html) - Provides the options to Export the grid data to Excel, PDF, and CSV formats.
* [**RTL support**](./global-local/#right-to-left-rtl): Provides right-to-left mode that aligns the grid content from right to left.
* [**Localization**](./global-local/#localization): Provides an inherent support to localize the UI.