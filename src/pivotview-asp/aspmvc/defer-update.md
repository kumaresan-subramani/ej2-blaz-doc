---
title: "Defer Layout Update"
component: "Pivot Table"
description: "Defer update allows users to update the pivot table only on demand."
---

# Defer Layout Update

Defer layout update support allows to update the pivot table component only on demand. On enabling this feature, end user can drag-and-drop fields between row, column, value and filter axes, apply sorting and filtering inside the Field List, resulting in change of pivot report alone but not the pivot table values. Once all operations are performed and on clicking the "Apply" button in the Field List, pivot table will start to update with the last modified report. This also helps in bringing better performance in pivot table component rendering.

The field list can be displayed in two different formats to interact with pivot table. They are:

* **In-built Field List (Popup)**: To display the field list icon in pivot table UI to invoke the built-in dialog.
* **Stand-alone Field List (Fixed)**: To display the field list in a static position within a web page.

## In-built Field List (Popup)

To enable deferred updates in the pivot table, set the property [`AllowDeferLayoutUpdate`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowDeferLayoutUpdate.html) in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) as **true**. To make a note, the defer update option can be controlled only via Field List during runtime.

{% aspTab template="pivot-table/defer-update/popup", sourceFiles="DeferUpdate.cs" %}

{% endaspTab %}

![output](images/fieldlist_deferupdate.png)

## Stand-alone Field List (Fixed)

The field list can be rendered in a static position, anywhere in web page layout, like a separate component. To do so, you need to set [`RenderMode`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~RenderMode.html) property to [**Mode.Fixed**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Mode.html) in [`PivotFieldList`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList_members.html).

To enable deferred updates in the static fieldlist, set the property [`AllowDeferLayoutUpdate`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList~AllowDeferLayoutUpdate.html) in [`PivotFieldlist`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotFieldList_members.html) as **true**. To make a note, the defer update option can be controlled only via Field List during runtime.

> To make field list interact with pivot table, you need to use the **UpdateView** and **Update** methods for data source update in both field list and pivot table simultaneously.

{% aspTab template="pivot-table/defer-update/static", sourceFiles="Static.cs" %}

{% endaspTab %}

![output](images/defer-update-static.png)