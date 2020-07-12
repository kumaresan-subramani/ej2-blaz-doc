# Tooltip

Tooltip is used to display details about the items in tree map when the mouse hovers over the item.

## Default tooltip

By default, tooltip is not visible. You can enable the tooltip by setting the `enable` property to true and injecting the `TreeMapTooltip` module using the `TreeMap.Inject(TreeMapTooltip)`.

The following example shows the default tooltip.

{% aspTab template="treemap/tooltip/tooltip", sourceFiles="tooltip.cs" %}

{% endaspTab %}

## Format tooltip

By default, tooltip shows information about weight value of current item. In addition, to show more information in tooltip, format the tooltip as `${datafield}` from data source.

The following example shows formatting the tooltip.

{% aspTab template="treemap/tooltip/format", sourceFiles="format.cs" %}

{% endaspTab %}

## Tooltip template

Any HTML element can be displayed in tooltip using the ‘template’ property. You can use `${datafield}` as placeholder in HTML element to display the values from data source.

The following example shows tooltip template.

{% aspTab template="treemap/tooltip/template", sourceFiles="template.cs" %}

{% endaspTab %}