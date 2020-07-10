---
title: "Field List"
component: "Pivot Table"
description: "Field list allows the user to add or remove fields and also re-arrange them between different axes."
---

# Pivot Field List

The pivot table provides a built-in Field List similar to Microsoft Excel. It allows to add or remove fields and also rearrange them between different axes, including column, row, value, and filter along with sort and filter options dynamically at runtime.

The field list can be displayed in two different formats to interact with pivot table. They are:

* **In-built Field List (Popup)**: To display the field list icon in pivot table UI to invoke the built-in dialog.
* **Stand-alone Field List (Fixed)**: To display the field list in a static position within a web page.

## In-built Field List (Popup)

To enable the field list in pivot table UI, set the [`ShowFieldList`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~ShowFieldList.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) class to **true**. A small icon will appear on the top left corner of the pivot table and clicking on this icon, field list dialog will appear.

> The field list icon will be displayed at the top right corner of the pivot table, when grouping bar is enabled.

{% aspTab template="pivot-table/getting-start-mvc/fieldlist", sourceFiles="fieldlist.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD012 -->
![output](images/gs_fieldlist_icon.png "Field list icon at the top left of the pivot table component")
<br/>
![output](images/gs_fieldlist_dialog.png "Field list dialog for user interaction")


## Stand-alone Field List (Fixed)

The field list can be rendered in a static position, anywhere in web page layout, like a separate component. To do so, you need to set [`RenderMode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~RenderMode.html) property to [**Mode.Fixed**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Mode.html) in [`PivotFieldList`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList_members.html).

> To make field list interact with pivot table, you need to use the **UpdateView** and **Update** methods for data source update in both field list and pivot table simultaneously.

{% aspTab template="pivot-table/field-list/static", sourceFiles="Static.cs" %}

{% endaspTab %}

![output](images/staticfieldlist.png "Static FieldList")

## Invoking dynamic Field List (Customized)

Also, you can display the field list dialog independently through other means. For example, you can invoke the field list dialog on an external button click. To do so, set [`RenderMode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~RenderMode.html) property to [**Mode.Popup**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Mode.html) and  since on button click, field list dialog will be invoked.

> * Meanwhile, you can display the field list dialog at specific target element within a webpage using `target` property. By default, the `target` value is null, which refers the `document.body` element.
> * Moreover, to make field list interact with pivot table, you need to use the **updateView** and **update** methods for data source update in both field list and pivot table simultaneously.

The below sample code illustrates the field list dialog invoked on an external button click.

{% aspTab template="pivot-table/field-list/popup", sourceFiles="Popup.cs" %}

{% endaspTab %}

![output](images/fieldlist-custom.png "FieldList in Button")

## Add or remove fields

Using check box besides each field, end user can select or unselect to add or remove fields respectively from the report at runtime.

![output](images/fieldlist_treeview.png)

## Remove specific field(s) from displaying

When a data source is bound to the component, fields will be automatically populated inside the Field List. In such case, user can also restrict specific field(s) from displaying. To do so, set the appropriate field name(s) in [`ExcludeFields`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ExcludeFields.html) property belonging to [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) class.

{% aspTab template="pivot-table/field-list/exclude-fields", sourceFiles="fieldlist.cs" %}

{% endaspTab %}

![output](images/fieldlist_hide.png)

## Re-arranging fields

In-order to re-arrange, drag any field from the field list and drop it into the column, row, value, or filter axis using the drag-and-drop holder. It helps end user to alter the report at runtime.

![output](images/fieldlist_axes.png)

## Filtering members

Using the filter icon besides each field in row, column and filter axes, members can be either included or excluded at runtime. To know more about member filtering, [`refer`](./filtering) here.

![output](images/fieldlist_filtericon.png "Filter icon besides each field")
<br/>
![output](images/fieldlist_editor.png "Filter dialog to either include or exclude members")
<br/>
![output](images/fieldlist_filteringgrid.png "Resultant pivot table on filtering members")

## Sorting members

Using the sort icon besides each field in row and column axes, members can be arranged either in ascending or descending order at runtime. To know more about member sorting, [`refer`](./sorting) here.

![output](images/fieldlist_sorticon.png "Sort icon besides each field")
<br/>
![output](images/fieldlist_sortgrid.png "Resultant pivot table showing countries in descending order")

## Calculated fields

The calculated field support allows end user to add a new calculated field based on the available fields from the bound data source using basic arithmetic operators. To enable this support in Field List UI, set the [`AllowCalculatedField`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowCalculatedField.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) class to **true** in pivot table. Now a button will be seen automatically inside the field list UI which will invoke the calculated field dialog on click. To know more about calculated field, [`refer`](./calculated-field) here.

![output](images/gs_calc_button.png "Enabling calculated field in field list UI")
<br/>
![output](images/gs_calc_dialog.png "Creating new calculated field")
<br/>
![output](images/gs_calc_grid.png "New calculated field 'Total Amount' added in pivot table")

## Changing aggregation type of value fields at runtime

End user can perform calculations over a group of values using the aggregation option. The value fields bound to the field list, appears with a dropdown icon, helps to select an appropriate aggregation type at runtime. On selection, the values in the Pivot Table will be changed dynamically. To know more about aggregation, [`refer`](./aggregation) here.

![output](images/aggregation_fl_icon.png "Icon to change aggregation type")
<br/>
<br/>
![output](images/fieldlist_aggregation_avg.png "List of pre-defined aggregation types")
<br/>
![output](images/fieldlist_aggregation_grid.png "Resultant pivot table showing average aggregation type applied in 'Unit Sold' value field")

## Defer layout update

Defer layout update support to update the pivot table only on demand and not during every user action. To enable this support in Field List UI, set the [`AllowDeferLayoutUpdate`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowDeferLayoutUpdate.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) class to **true** in pivot table. Now a check box inside Field List UI will be seen in checked state, allowing pivot table to update only on demand. To know more about defer layout, [`refer`](./defer-update) here.

![output](images/fieldlist_deferupdate.png)

## Show field list using toolbar

It can also be viewed in toolbar by setting [`ShowFieldList`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowDeferLayoutUpdate.html) and [`ShowToolbar`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowDeferLayoutUpdate.html) properties in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) class to **true**. Also, include the item **FieldList** within the [`Toolbar`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowDeferLayoutUpdate.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) class. When toolbar is enabled, field list icon will be automatically added into the toolbar and the icon won't appear on top left corner in the pivot table component.

{% aspTab template="pivot-table/field-list/toolbar", sourceFiles="fieldlist.cs" %}

{% endaspTab %}

![output](images/fieldlist_toolbar.png)

## Set caption to fields which isn’t bound to the report

One can set the caption to all fields from the data source even if it is not bound to the actual report. It can be achieved using the [`EnginePopulated`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~EnginePopulated.html) event. On doing so, caption of the respective field will be displayed in both grouping bar and field list.

In the sample, we have set caption to the fields `Year` and `Quarter` dynamically.

{% aspTab template="pivot-table/field-list/fieldlist-caption", sourceFiles="fieldlist.cs" %}

{% endaspTab %}

![output](images/fieldlist_caption1.png)

## Events

### EnginePopulated

The [`EnginePopulated`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~EnginePopulated.html) event is available in both Pivot Table and Field List.

* The event [`EnginePopulated`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~EnginePopulated.html) is triggered in field list whenever the report gets modified. The updated report is passed to the pivot table via `UpdateView` method written within this event to refresh the same.

* Likewise, [`EnginePopulated`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~EnginePopulated.html) event is triggered in pivot table whenever the report gets modified. The updated report is passed to the field list via `Update` method written within this event to refresh the same.

The event [`EnginePopulated`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~EnginePopulated.html) is triggered after engine is populated. It has following parameters - `DataSourceSettings`, `PivotFieldList` and `PivotValues`.

> Note: This event is not required for Popup field list since it is a in built one.

{% aspTab template="pivot-table/field-list/static", sourceFiles="Static.cs" %}

{% endaspTab %}


### FieldListRefreshed

The event [`FieldListRefreshed`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~FieldListRefreshed.html) is triggered whenever there is any change done in the field list UI. It has following parameter - `DataSourceSettings` and `PivotValues`. It allows user to identify each field list update. This event is applicable only for static field list.

{% aspTab template="pivot-table/field-list/refresh-event", sourceFiles="Popup.cs" %}

{% endaspTab %}


### FieldDropped

The event [`OnFieldDropped`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~OnFieldDropped.html) fires whenever a field is dropped in an axis. It has following parameters - `DroppedAxis`, `DroppedField` and `DataSourceSettings`. In this illustration, we have modified the `DroppedField` caption through this event at runtime.

{% aspTab template="pivot-table/field-list/field-dropped", sourceFiles="dropped.cs" %}

{% endaspTab %}

![output](images/fielddropped_fieldlist.png)

## See Also

* [Change load limited data in member editor](./how-to/change-load-limited-data-in-member-editor)
* [Customize the icons for pivot table](./how-to/customize-the-icons-for-pivot-table)