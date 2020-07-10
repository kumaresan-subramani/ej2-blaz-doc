---
title: "Conditional Formatting"
component: "Pivot Table"
description: "Conditional formatting allowing the users to highlighting the value cells based on its value."
---

# Conditional Formatting

Allows end user to change the appearance of the pivot table value cells with its background color, font color, font family, and font size based on specific conditions.

The conditional formatting can be applied at runtime through the built-in dialog, invoked from the toolbar. To do so, set [`AllowConditionalFormatting`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~AllowConditionalFormatting.html) and [`ShowToolbar`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~ShowToolbar.html) properties in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) class to **true**. Also, include the item **ConditionalFormatting** within the [`Toolbar`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView~Toolbar.html) property in [`PivotView`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotView_members.html) class. End user can now see the "Conditional Formatting" icon in toolbar UI automatically, which on clicking will invoke the formatting dialog to perform necessary operations.

{% aspTab template="pivot-table/conditional-formatting/tool-bar", sourceFiles="Formatting.cs" %}

{% endaspTab %}

<!-- markdownlint-disable MD012 -->
![output](images/toolbar_cformatting.png "Conditional formatting icon in toolbar")
<br/>
<br/>
![output](images/toolbar_cformatting_dialog.png "Adding new conditional format")
<br/>
<br/>
![output](images/toolbar_cformatting_dialog_apply.png "Setting conditional format criteria")
<br/>
<br/>
![output](images/toolbar_cformatting_grid.png "Resultant pivot table on applied conditional format")

Conditional formatting can also be included in the pivot table through code-behind using the [`PivotViewConditionalFormatSetting`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting_members.html) class. The required properties to apply a new conditional formatting are,

* [`Measure`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting~Measure.html): Specifies the value field name for which style will be applied.
* [`Conditions`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting~Conditions.html): Specifies the operator type such as equals, greater than, less than, etc.
* [`Value1`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting~Value1.html): Specifies the start value.
* [`Value2`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting~Value2.html): Specifies the end value.
* [`PivotViewStyle`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewStyle_members.html): Specifies the style for the cell.

The available style properties in [`PivotViewStyle`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewStyle_members.html) class, to set in value cells are:

* [`BackgroundColor`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewStyle~BackgroundColor.html): Specifies the background color.
* [`Color`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewStyle~Color.html): Specifies the font color.
* [`FontFamily`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewStyle~FontFamily.html): Specifies the font family.
* [`FontSize`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewStyle~FontSize.html): Specifies the font size.

Meanwhile, user can also view conditional formatting dialog in UI by invoking `ShowConditionalFormattingDialog` method on an external button click which is shown in the below code sample.

{% aspTab template="pivot-table/conditional-formatting/ui", sourceFiles="Formatting.cs" %}

{% endaspTab %}

![output](images/cond-format-btn.png)

![output](images/cond-format-btn2.png)

## Conditional formatting for all fields

Allows end user to apply conditional formatting commonly for all value fields just by ignoring the [`Measure`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting~Measure.html) property and setting rest of the properties in [`PivotViewConditionalFormatSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting_members.html) class.

{% aspTab template="pivot-table/conditional-formatting/code-behind", sourceFiles="Formatting.cs" %}

{% endaspTab %}

![output](images/cformatting_all.png)

## Conditional formatting for specific value field

Allows end user to apply conditional formatting to a specific value field by setting the [`Measure`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting~Measure.html) property with specific value field name in [`PivotViewConditionalFormatSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewConditionalFormatSetting_members.html) class.

{% aspTab template="pivot-table/conditional-formatting/code-behind-specific", sourceFiles="Formatting.cs" %}

{% endaspTab %}

![output](images/cformatting_single.png)

## Editing and removing existing conditional format

Editing and removing existing conditional format can be done through the UI at runtime. To do so, open the conditional formatting dialog and edit the "Value", "Condition" and "Format" options based on user requirement and click "OK". To remove a conditional format, click the "Delete" icon besides the respective condition.  

![output](images/cformatting_remove.png)

## Event

### ConditionalFormatting

The event `ConditionalFormatting` is triggered initially while clicking the “ADD CONDITION” button inside the conditional formatting dialog in-order to fill user specific condition instead of default condition at runtime. To use this event, `AllowConditionalFormatting` property in PivotView must be set to **true**. It has following parameters -

* `applyGrandTotals` - boolean property, by setting this to true user can enable formatting to grand totals.
* `conditions` - condition to be filled in conditional formatting dialog.
* `label` - Label value for conditional formatting dialog.
* `measure` - measure value for the conditional formatting dialog.
* `style` - style property of the conditional formatting dialog.
* `value1` - value 1 for conditional formatting dialog.
* `value2` - value 2 for conditional formatting dialog, this is applicable only for selected conditions like **Between** and **NotBetween**.

{% aspTab template="pivot-table/conditional-formatting/event", sourceFiles="Formatting.cs" %}

{% endaspTab %}

## See Also

* [Apply conditional formatting for specific row or column](./how-to/apply-conditional-formatting-for-specific-row-or-column)
