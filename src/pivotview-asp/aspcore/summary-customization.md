---
title: "Show or hide totals"
component: "Pivot Table"
description: "Show/hide sub-totals and grand totals for the pivot table"
---

# Show or hide totals

## Show or hide grand totals

Allows to show or hide grand totals in rows and columns using the [`showGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowGrandTotals.html) property. To hide the grand totals in rows and columns, set the property [`showGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowGrandTotals.html) in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag to **false**.
End user can also hide grand totals for row or columns separately by setting the property [`showRowGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowRowGrandTotals.html) or [`showColumnGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowColumnGrandTotals.html) in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag to **false** respectively.

> By default, [`showGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowGrandTotals.html), [`showRowGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowRowGrandTotals.html) and [`showColumnGrandTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowColumnGrandTotals.html) properties in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag are set as **true**.

{% aspTab template="pivot-table/summary-customization/grand-total", sourceFiles="GrandTotal.cs" %}

{% endaspTab %}

![output](images/grandtotal.png)

## Show or hide sub-totals

Allows to show or hide sub-totals in rows and columns using the [`showSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowSubTotals.html) property. To hide all the sub-totals in rows and columns, set the property [`showSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowSubTotals.html) in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag to **false**. End user can also hide sub-totals for rows or columns separately by setting the property [`showRowSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowRowSubTotals.html) or [`showColumnSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowColumnSubTotals.html) in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag to **false** respectively.

> By default, [`showSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowRowSubTotals.html), [`showRowSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowRowSubTotals.html) and [`showColumnSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ShowColumnSubTotals.html) in [`e-datasourcesettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) tag are set as **true**.

{% aspTab template="pivot-table/summary-customization/sub-total", sourceFiles="SubTotal.cs" %}

{% endaspTab %}

![output](images/sub-total.png)

## Show or hide sub-totals for specific fields

Allows to show or hide sub-totals for specific fields in rows and columns using the [`showSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewRow~ShowSubTotals.html)) property. To hide sub-totals for a specific field in row or column axis, set the property [`showSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewRow~ShowSubTotals.html) property in [`e-rows`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewRow_members.html) or [`e-columns`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.ColumnsDataSourceSettings_members.html) tag to **false** respectively.

> By default, [`showSubTotals`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewRow~ShowSubTotals.html) property in [`e-rows`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewRow_members.html) or [`e-columns`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.ColumnsDataSourceSettings_members.html) tag is set as **true**.

{% aspTab template="pivot-table/summary-customization/sub-total-specific", sourceFiles="SubTotalSpecific.cs" %}

{% endaspTab %}

![output](images/subtotal2.png)

## Show or hide totals using toolbar

It can also be achieved using built-in toolbar options by setting the [`showToolbar`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~ShowToolbar.html) property in [`ejs-pivotview`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) tag to **true**. Also, include the items **GrandTotal** and **SubTotal** within the [`toolbar`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Toolbar.html) property in [`ejs-pivotview`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) tag. End user can now see "Show/Hide Grand totals" and "Show/Hide Sub totals" icons in toolbar UI automatically.

{% aspTab template="pivot-table/summary-customization/toolbar", sourceFiles="Toolbar.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD012 -->
![output](images/grand_toolbar.png)
<br/>
<br/>
<br/>
![output](images/sub_toolbar.png)
