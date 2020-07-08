---
title: "Use Edit Template in Foreign Key Column"
component: "Grid"
description: "Learn how to use Edit Template in Foreign Key Column."
---

# Use Edit Template in Foreign Key Column

By default, foreign key column uses dropdown component for editing. You can render other than the dropdown by using the [`edit`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Edit.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) tag helper. The following example demonstrates the way of using edit template in foreign column.

In the following example, The **Employee Name** is a foreign key column and while editing, AutoComplete component is rendered instead of DropDownList.

{% aspTab template="grid/how-to/edit-template-foreign", sourceFiles="edit-template-foreign.cs" %}

{% endaspTab %}
