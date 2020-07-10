---
title: "Filtering"
component: "Pivot Table"
description: "Filtering allows user to view pivot table with particular records based on selected members."
---

# Filtering

Filtering allows to view the pivot table with selective records based on members that can be either included or excluded through UI and code-behind.

The following are the three different types of filtering:

* Member filtering
* Label filtering
* Value filtering

> When all the above filtering options are disabled via code-behind, then the filter icon would be disabled in the field list or grouping bar UI.

## Member filtering

Allows to view the pivot table with selective records based on included and excluded members in each field. By default, member filter option is enabled by the [`AllowMemberFilter`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~AllowMemberFilter.html) boolean property in [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) class. This UI option helps end user to filter members by clicking the filter icon besides any field in the row, column and filter axes available in the field list or grouping bar UI at runtime.

![output](images/fieldlist_filtericon.png "Member filter icon in field list")
<br/>
![output](images/filter_icon_gb.png "Member filter icon in grouping bar")
<br/>
![output](images/filter_dialog_gb.png "Member filter dialog with checked and unchecked members")
<br/>
![output](images/filter_grid_gb.png "Resultant pivot table on member filter")

Meanwhile filtering can also be configured at code behind using the [`PivotViewFilterSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html) class while initial rendering of the component. The basic settings required to add filter criteria are:

* [`Name`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Name.html): It allows to set the appropriate field name.
* [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html): It allows to set the filter type as [**FilterType.Include**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.FilterType.html) or [**FilterType.Exclude**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.FilterType.html) to include or exclude field members respectively.
* [`Items`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Items.html): It allows to set the members which needs to be either included or excluded from display.
* [`LevelCount`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~LevelCount.html): It allows to set level count of the field to fetch data from the cube. **NOTE: This property applicable only for OLAP data source.**

> When specifying unavailable or inappropriate members to include or exclude filter items collection, they will be ignored.

{% aspTab template="pivot-table/filtering/member-filtering", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/member-filtering.png)

### Option to select and unselect all members

The member filter dialog comes with an option "All", which on checked selects all members and on unchecked deselects all members. The option "All" would appear in intermediate state mentioning that both selected and unselected child members are available.

![output](images/editor_inter.png)

When all members are deselected, the "Ok" button in member filter dialog would be disabled, meaning, at least one member should be selected and bound to the pivot table component.

![output](images/editor_alluncheck.png)

### Provision to search specific member(s)

By default, search option is available to quickly navigate to the desired members. It can be done by entering the starting character(s) of the actual members.

![output](images/search.png)

### Option to sort members

User can sort members within the member editor either to ascending (or) descending using the built-in sort icons. When both ascending and descending options are not chosen, then members will be shown in the default order (retrieved as such from data source).

![output](images/member-sort.png)

### Performance Tips

In member filter dialog, end user can set the limit to display members while loading large data. Based on this limit, initial loading will get completed quickly without any performance constraint. Also, a message with remaining member count, which are not part of the UI, will be displayed in the member editor.

The data limit can be set using the [`MaxNodeLimitInMemberEditor`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~MaxNodeLimitInMemberEditor.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_properties.html) class. By default, the property holds the numeric value **1000**.

{% aspTab template="pivot-table/filtering/max-node", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/maxnodelimit.png)

Meanwhile, end user can utilize the search option to refine the members from the exceeded limit. For example, consider that there are 5000 members in the name "Node 1", "Node 2", "Node 3", and so on... and user has set the property [`MaxNodeLimitInMemberEditor`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~MaxNodeLimitInMemberEditor.html) to **500**. In this case, only the initial 500 members will be displayed by default leaving a message "4500 more items. Search to refine further.". To get the member(s) between 501 to 5000, enter the starting character(s) in search option to bring the desired member(s) from the exceeded limit to the UI. Now, end user can either check or uncheck to continue with the filtering process.

![output](images/maxnodelimit_search.png)

### Loading members on-demand

> This property is applicable only for OLAP data sources.

Allows to load members inside the filter dialog on-demand by setting the [`LoadOnDemandInMemberEditor`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~LoadOnDemandInMemberEditor.html) property to **true**. By default, first level is loaded in the member editor from the OLAP cube. So, the member editor will be opened quickly, without any performance constraints. By default, this property is set to **true** and the search will only be applied to the level members that are loaded. In the meantime, the next level members can be added using either of the following methods.

* By clicking on the expander button of the respective member, only its child members will be loaded.
* Select a level from the drop-down list that will load all members up to the chosen level from the cube.

This will help to avoid performance lags when opening a member editor whose hierarchy has a large number of members. Once level members are queried and added one after the other, they will be maintained internally (for all operations like dialog re-opening, drag and drop, etc...) and will not be removed until the web page is refreshed.

{% aspTab template="pivot-table/getting-start-mvc/olap-member-load", sourceFiles="filtering.cs" %}

{% endaspTab %}

![output](images/ondemand_member.png)

In the example above, "Customer Geography" dimension is loaded with first level (Country) during initial loading. The search will therefore be applied on the members of the "Country" level alone. After that, you can load members to the next level (State-Province) on-demand by expanding the "Australia" node (or) by selecting the "State-Province" level from the drop down list.

* When you expand "Australia", the "State-Province" members will be loaded to "Australia" alone.
* If you load the members by selecting the "State-Province" level from the drop-down list means, the "State-Province" members will be loaded across all countries like Australia, Canada, France, etc...

Once members are loaded, they are maintained internally and will not be removed until the page is refreshed.

If the property is set to **false**, all members of all levels will be queried and added during initial loading itself. Only one query is executed here to retrieve all members from all levels. Since it fetches large number of members, you can feel the performance difference while opening the member editor. But still, expand and search operation is quick here because the members have already been retrieved and populated.

![output](images/initial_member.png)

### Loading members based on level number

> This property is applicable only for OLAP data sources.

Allows user to load the members on the basis of the level number set in the [`LevelCount`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~LevelCount.html) property in the [`PivotViewFilterSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html). By default, this property is set to **1** and the search will only take place within the members of the first level.

{% aspTab template="pivot-table/getting-start-mvc/olap-level-count", sourceFiles="filtering.cs" %}

{% endaspTab %}

![output](images/level-count.png)

In the example above, we set [`LevelCount`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~LevelCount.html) as **2** for the "Customer Geography" dimension in [`PivotViewFilterSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html). So, the "Customer Geography" dimension is loaded with the "Country" and "State-Province" levels during initial loading itself. The search will therefore be applied only to the members of the "Country" and "State-Province" levels. After that, you can load members to the next level on-demand by expanding the respective "State-Province" node (or) by selecting the "City" level from the drop-down list.

## Label filtering

The label filtering helps to view the pivot table with selective header text in fields across row and column axes based on the applied filter criteria. The following are the three different types of label filtering available:

* Filtering string data type
* Filtering number data type
* Filtering date data type

The label filtering dialog can be enabled by setting the [`AllowLabelFilter`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~AllowLabelFilter.html) property in [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) class to **true**. After enabling this API, click the filter icon besides any field in row or column axis available in field list or grouping bar UI. Now a filtering dialog will appear and navigate to "Label" tab to perform label filtering operations.

{% aspTab template="pivot-table/filtering/label-filtering/filtering-ui", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/labelfiltering_fl_icon.png "Filter icon in field list")
<br/>
![output](images/labelfiltering_gb_icon.png "Filter icon in grouping bar")
<br/>
<br/>
![output](images/labelfiltering_dialog.png "Label filter tab in member editor dialog")
<br/>
<br/>
![output](images/labelfiltering_grid.png "Resultant pivot table on label filter")

> In label filtering UI, based on the field chosen, it’s member data type is automatically recognized and filtering operation will be carried out. Where as in code behind, user need to define the data type through a property and it has been explained in the immediate section below.

### Filtering string data type through code

This type of filtering is exclusively applicable for fields with members in string data type. The filtering can be configured using the [`PivotViewFilterSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html) class through code-behind. The properties required for label filter are:

* [`Name`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Name.html): Sets the field name.
* [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html): Sets the filter type as [**FilterType.Label**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.FilterType.html) to the field.
* [`Condition`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Condition.html): Sets the operator type such as [**Operators.Equals**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.GreaterThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.LessThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), etc.
* [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value1.html): Sets the start value.
* [`Value2`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value2.html): Sets the end value. It is applicable only for the operator such as [**Operators.Between**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) and [**Operators.NotBetween**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html).
* [`SelectedField`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~SelectedField.html): Sets level name of a dimension, where the filter settings are to be applied. **NOTE: This property applicable only for OLAP data source.**

For example, in a "Country" field, to show countries names that contains "United" text alone, set [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value1.html) to "United" and [`Condition`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Condition.html) to [**Operators.Contains**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) for desired output in pivot table.
[**Operators**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) that can be used in label filtering are:

| Operator | Description |
|------|-------------|
| Equals| Displays the pivot table that matches with the text.|
| DoesNotEquals| Displays the pivot table that does not match with the given text.|
| BeginWith| Displays the pivot table that begins with text.|
| DoesNotBeginWith| Displays the pivot table that does not begins with text.|
| EndsWith| Displays the pivot table that ends with text.|
| DoesNotEndsWith| Displays the pivot table that does not ends with text.|
| Contains| Displays the pivot table that contains text.|
| DoesNotContains| Displays the pivot table that does not contain text.|
| GreaterThan| Displays the pivot table when the text is greater.|
| GreaterThanOrEqualTo| Displays the pivot table when the text is greater than or equal.|
| LessThan| Displays the pivot table when the text is lesser.|
| LessThanOrEqualTo| Displays the pivot table when the text is lesser than or equal.|
| Between| Displays the pivot table that records between the start and end text.|
| NotBetween| Displays the pivot table that does not record between the start and end text.|

{% aspTab template="pivot-table/filtering/label-filtering/text-filtering", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/labelfiltering_code.png)

### Filtering number data type through code

This type of filtering is exclusively applicable for fields with members in number data type. The filtering can be configured in a similar way explained in the previous section - "Filtering string data type through code", except the [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html) property setting. For number data type, set the [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html) property to [**FilterType.Number**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.FilterType.html) enumeration.

For example, in a "Sold" field, to show the values between "90" to "100", set [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value1.html) to "90", [`Value2`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value2.html) to "100" and [`Condition`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Condition.html) to [**Operators.Between**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) for desired output in pivot table.

> Operators like [**Operators.Equals**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.DoesNotEquals**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.GreaterThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.GreaterThanOrEqualTo**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.LessThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.LessThanOrEqualTo**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.Between**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), and [**Operators.NotBetween**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) are alone applicable for number data type.

{% aspTab template="pivot-table/filtering/label-filtering/number-filtering", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/numberfiltering.png)

### Filtering date data type through code

This type of filtering is exclusively applicable for fields with members in date data type. The filtering can be configured in a similar way explained in the prior section - "Filtering string data type through code", except the [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html) property setting. For date data type, set the [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html) property to [**FilterType.Date**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.FilterType.html) enumeration.

For example, in a "Delivery Date" field, to show the records of the the year after 2015, then set [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value1.html) to "2015-01-01" and [`Condition`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Condition.html) to [**Operators.After**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) for desired output in pivot table.

> Operators like [**Operators.Equals**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.DoesNotEquals**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.Before**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.BeforeOrEqualTo**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.After**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.AfterOrEqualTo**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.Between**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), and [**Operators.NotBetween**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) are alone applicable for date data type.

{% aspTab template="pivot-table/filtering/label-filtering/date-filtering", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/datefiltering.png)

### Clearing the existing label filter

End user can clear the applied label filter by simply click the "Clear" option at the bottom of the filter dialog under "Label" tab.

![output](images/clearfilter.png)

## Value filtering

The value filtering helps to perform filter operation based only on value fields and its resultant aggregated values over other fields defined in row and column axes.

The value filtering dialog can be enabled by setting the [`AllowValueFilter`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~AllowValueFilter.html) property in [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) class to **true**. After enabling this API, click the filter icon besides any field in row or column axis available in field list or grouping bar UI. Now a filtering dialog will appear and navigate to "Value" tab to perform value filtering operations.

{% aspTab template="pivot-table/filtering/value-filtering-ui", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/labelfiltering_fl_icon.png "Filter icon in field list")
<br/>
![output](images/labelfiltering_gb_icon.png "Filter icon in grouping bar")
<br/>
<br/>
![output](images/valuefiltering_dialog.png "Value filter tab in member editor dialog")
<br/>
<br/>
![output](images/valuefiltering_grid.png "Resultant pivot table on value filter")

The value filtering can also be configured using the [`PivotViewFilterSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html) class through code-behind. The properties required for value filter are:

* [`Name`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Name.html): Sets the normal field name.
* [`Type`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Type.html): Sets the filter type as [**FilterType.Value**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.FilterType.html) to the field.
* [`Measure`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Measure.html): Sets the value field name.
* [`Condition`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Condition.html): Sets the operator type such as [**Operators.Equals**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.GreaterThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html), [**Operators.LessThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) etc.
* [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value1.html): Sets the start value.
* [`Value2`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value2.html): Sets the end value. It is applicable only for the operator such as [**Operators.Between**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) and [**Operators.NotBetween**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html).

For example, to show the data where total sum of units sold for each country exceeding 1500, set [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Value1.html) to "1500" and [`Condition`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting~Condition.html) to [**Operators.GreaterThan**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) in the "Country" field.

[**Operators**](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.Operators.html) that can be used in value filtering are:

| Operator | Description |
|------|-------------|
| Equals| Displays the pivot table that matches with the value.|
| DoesNotEquals| Displays the pivot table that does not match with the given value.|
| GreaterThan| Displays the pivot table when the value is greater.|
| GreaterThanOrEqualTo| Displays the pivot table when the value is greater than or equal.|
| LessThan| Displays the pivot table when the value is lesser.|
| LessThanOrEqualTo| Displays the pivot table when the value is lesser than or equal.|
| Between| Displays the pivot table that records between start and end values.|
| NotBetween| Displays the pivot table that does not record between start and end values.|

{% aspTab template="pivot-table/filtering/value-filtering", sourceFiles="Filtering.cs" %}

{% endaspTab %}

![output](images/valuefiltering_grid.png)

### Clearing the existing value filter

End user can clear the applied value filter by simply click the "Clear" option at the bottom of the filter dialog under "Value" tab.

![output](images/clearvaluefilter.png)

## Event

### MemberFiltering

The event `memberFiltering` triggers before applying filter using the dialog, that is, specifically while clicking the **"OK"** button. Using this event user can view or modify the applied [filter settings](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html) such as filter items, type of filter, conditions, etc. It has following parameters:

* `cancel` - Boolean property, when the parameter `cancel` is set to **true**, applied filtering will not be updated
* [`filterSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html) - It holds current [filter settings](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewFilterSetting_members.html).
* `dataSourceSettings` - It holds updated datasource settings.

{% aspTab template="pivot-table/filtering/member-filtering-event", sourceFiles="Filtering.cs" %}

{% endaspTab %}

### MemberEditorOpen

The event [`MemberEditorOpen`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~MemberEditorOpen.html) fires while opening member editor dialog. It allows to customize the field members to be displayed in the dialog. It has the following parameters

* `fieldName`: It holds the name of the appropriate field.

* `fieldMembers`: It holds the members of a field.

* `cancel`: It is a boolean property and by setting this to true, dialog won’t be created.

In the below sample, the member editor of field "Country" shows only the selected Item.

{% aspTab template="pivot-table/filtering/memberEditorOpen-event", sourceFiles="Filtering.cs" %}

{% endaspTab %}