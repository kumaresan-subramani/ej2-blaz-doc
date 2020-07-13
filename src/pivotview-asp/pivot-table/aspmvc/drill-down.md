---
title: "Drill Down"
component: "Pivot Table"
description: "Expand or collapse headers displayed in rows and columns."
---

# Drill Down

## Drill down and drill up

The drill down and drill up action helps to view the bound data in detailed and abstract view respectively. By default, if member(s) has children, then expand and collapse icon will be displayed in the respective row/column header. On clicking the icon, expand or collapse action will be performed automatically through built-in source code. Meanwhile, leaf member(s) does not contain expand and collapse icon.

![output](images/drill.png)

## Drill position

Allows to drill only the current position of the selected member and exclude the drilled data of selected member in other positions. For example, if "FY 2015" and "FY 2016" have "Q1" member as child in next level, and when end user attempts to drill "Q1" under "FY 2016", only it will be expanded and not "Q1" under "FY 2015".

> This feature is built-in and occurs every time when expand or collapse action is done for better performance.

![output](images/drill_position.png)

## Expand all

> This property is applicable only for the relational data source.

Allows to either expand or collapse all headers that are displayed in row and column axes. To display all headers in expanded state, set the property [`ExpandAll`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ExpandAll.html) to **true** and to collapse all
headers, set the property [`ExpandAll`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ExpandAll.html) to **false**. By default, [`ExpandAll`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ExpandAll.html) property is set to **false**.

{% aspTab template="pivot-table/drill-down/expand-all", sourceFiles="ExpandAll.cs" %}

{% endaspTab %}

![output](images/expandall.png)

## Expand all except specific member(s)

> This option is applicable only for the relational data source.

In addition to the previous topic, there is an enhancement to expand all headers expect specific header(s) and similarly to collapse all headers except specific header(s). To achieve this, [`PivotViewDrilledMember`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember_members.html) class is used. The required properties of the [`PivotViewDrilledMember`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember_members.html) class are explained below:

* [`Name`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember~Name.html): It allows to set the field name whose member(s) needs to be specifically drilled.
* [`Items`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember~Items.html): It allows to set the exact member(s) which needs to be drilled.

> The [`PivotViewDrilledMember`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember_members.html) option always works in vice-versa with respect to the property [`ExpandAll`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ExpandAll.html) in pivot table. For example, if [`ExpandAll`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~ExpandAll.html) is set to **true**, then the member(s) added in [`Items`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember~Items.html) collection alone will be in collapsed state.

{% aspTab template="pivot-table/drill-down/drilled-members", sourceFiles="DrilledMembers.cs" %}

{% endaspTab %}

![output](images/expandall_except.png)

## Expand specific member(s)

End user can also manually expand or collapse specific member(s) in each fields under row and column axes using the [`DrilledMembers`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember_members.html) class from code behind. The required properties of the [`DrilledMembers`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember_members.html) class are explained below:

* [`Name`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember~Name.html): It allows to set the field name whose member(s) needs to be specifically drilled.
* [`Items`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember~Items.html): It allows to set the exact member(s) which needs to be drilled.
* [`Delimiter`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDrilledMember~Delimiter.html): It allows to separate next level of member from its parent member.

{% aspTab template="pivot-table/drill-down/expand-specific", sourceFiles="DrilledMembers.cs" %}

{% endaspTab %}

![output](images/drill_position_code.png)

## Event

### Drill

The event `Drill` triggers every time when a field is expanded or collapsed. For instance using this event user can alter delimiter and drill action for the respective item. It has the following parameters:

* `drillInfo` - It holds the current drilled item information.
* `pivotview` - It holds pivot table instance.

{% aspTab template="pivot-table/drill-down/drill-event", sourceFiles="DrilledEvent.cs" %}

{% endaspTab %}