---
title: "How to show grouped rows based on the pageSize"
component: "Grid"
description: "Learn how to show the grouped row based on the pageSize"
---

# How to show grouped rows based on the pageSize

By default, we have displayed the no of records based on the [`PageSize`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridPageSettings~PageSize.html). If you want to show grouped column rows based on the [`PageSize`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridPageSettings~PageSize.html) then we suggest you to use the below way.

In the below sample, we have overridden the default **generateQuery** to display the grouped rows instead of grid rows based on the [`PageSize`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridPageSettings~PageSize.html).

{% aspTab template="grid/how-to/group-page-size", sourceFiles="group-page-size.cs" %}

{% endaspTab %}