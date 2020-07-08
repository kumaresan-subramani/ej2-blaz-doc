---
title: "Print"
component: "Grid"
description: "Learn how to print DataGrid content, set up pages for printing, perform external print, and print visible pages in the Essential JS 2 DataGrid control."
---

# Print

To print the Grid, use the **print** method from grid instance. The print option can be displayed on the [`toolbar`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Toolbar.html) by adding the **Print** toolbar item.

{% aspTab template="grid/print/print", sourceFiles="print.cs" %}

{% endaspTab %}

## Page setup

Some of the print options cannot be configured through JavaScript code. So, you have to customize the layout, paper size, and margin options using the browser page setup dialog. Please refer to the following links to know more about the browser page setup:

* [`Chrome`](https://support.google.com/chrome/answer/1069693?hl=en&visit_id=1-636335333734668335-3165046395&rd=1)
* [`Firefox`](https://support.mozilla.org/en-US/kb/how-print-web-pages-firefox)
* [`Safari`](http://www.mintprintables.com/print-tips/adjust-margins-osx/)
* [`IE`](http://www.helpteaching.com/help/print/index.htm)

## Print using an external button

To print the grid from an external button, invoke the **print** method.

{% aspTab template="grid/print/external-btn", sourceFiles="external-btn.cs" %}

{% endaspTab %}

## Print the visible page

By default, the grid prints all the pages. To print the current page alone, set the [`PrintMode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PrintMode.html) to **CurrentPage**.

{% aspTab template="grid/print/current-page", sourceFiles="current-page.cs" %}

{% endaspTab %}

## Print the hierarchy grid

By default, the grid will be print the master and expanded child grids alone. you can change the print option by using the [`hierarchyPrintMode`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~HierarchyPrintMode.html) property. The available options are,

| Mode     | Behavior    |
|----------|-------------|
| Expanded | Prints the master grid with expanded child grids. |
| All      | Prints the master grid with all the child grids. |
| None     | Prints the master grid alone. |

{% aspTab template="grid/print/hierarchyprint", sourceFiles="hierarchyprint.cs" %}

{% endaspTab %}

> By default, the hierarchy grid prints the expanded child grids from the visible page only. Refer [To Print the expanded state grid from all pages](./how-to/print-the-expanded-state-from-other-pages)

## Print large number of columns

By default, the browser uses A4 as page size option to print pages and to adapt the size of the page the browser print preview will auto-hide the overflowed contents. Hence grid with large number of columns will cut off to adapt the print page.

To show large number of columns when printing, adjust the scale option from print option panel based on your content size.

![Scale Option Setting](./images/print-preview.png)

## Show or Hide columns while Printing

You can show a hidden column or hide a visible column while printing the grid using [`toolbarClick`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ToolbarClick.html) and [`printComplete`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PrintComplete.html) events.

In [`toolbarClick`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ToolbarClick.html) event, based on **args.item.id** as **grid_print**. We can show or hide columns by setting [`visible`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Visible.html) property of **e-grid-column** to **true** or **false** respectively.

In [`printComplete`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~PrintComplete.html) event, We have reversed the state back to the previous state.

In the below example, we have **CustomerID** as a hidden column in the grid. While printing, we have changed **CustomerID** to visible column and **ShipCity** as hidden column.

{% aspTab template="grid/print/show-hide-columns", sourceFiles="show-hide.cs" %}

{% endaspTab %}

## Limitations of Printing Large Data

When grid contains large number of data, printing all the data at once is not a best option for the browser performance. Because to render all the DOM elements in one page will produce performance issues in the browser. It leads to browser slow down or browser hang. Grid have option to handle large number of data by Virtualization. However while printing, it is not possible to use virtualization for rows and columns.

If printing of all the data is still needed, we suggest to Export the grid to **Excel** or **CSV** or **Pdf** and then print it from another non-web based application.

## See Also

* [How to Print the expanded state grid from all pages](./how-to/print-the-expanded-state-from-other-pages)
