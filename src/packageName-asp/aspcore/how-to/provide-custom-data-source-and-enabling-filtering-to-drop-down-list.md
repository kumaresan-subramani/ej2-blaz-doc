---
title: "Provide custom data source and enabling filtering to DropDownList"
component: "Grid"
description: "Learn how to provide custom data source and enabling filtering to DropDownList."
---

# Provide custom data source and enabling filtering to DropDownList

You can provide data source to the DropDownList by using the **params** of [`edit`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Edit.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html).

While setting new data source using edit params, you must specify a new **query** property too for the DropDownList as follows,

```typescript
@{
    var DropDownList = new Syncfusion.EJ2.DropDowns.DropDownList() { DataSource = ViewBag.DropDownData, Query = "new ej.data.Query()", AllowFiltering = true, Fields = new Syncfusion.EJ2.DropDowns.DropDownListFieldSettings() { Value = "Country", Text = "Country" }, ActionComplete = "actionComplete" };
}
{
    <e-grid-column field="ShipCountry" headerText="Ship Country" width="150" editType="dropdownedit" edit="new {@params = DropDownList }"></e-grid-column>
}

```

You can also enable filtering for the DropDownList by passing the **allowFiltering** as **true** to the edit params.

In the below demo, DropDownList is rendered with custom Datasource for the **ShipCountry** column and enabled filtering to search DropDownList items.

{% aspTab template="grid/how-to/dropdown-edit", sourceFiles="edit-dropdownlist.cs" %}

{% endaspTab %}
