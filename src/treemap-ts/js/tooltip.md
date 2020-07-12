# Tooltip

Tooltip is used to display details about the items in tree map when the mouse hovers over the item.

## Default tooltip

By default, tooltip is not visible. You can enable the tooltip by setting the `enable` property to true.

The following example shows the default tooltip.

{% tab template= "treemap/tooltip", es5Template="es5Tooltip" %}

{% endtab %}

## Format tooltip

By default, tooltip shows information about weight value of current item. In addition, to show more information in tooltip, format the tooltip as `${datafield}` from data source.

The following example shows formatting the tooltip.

{% tab template= "treemap/tooltip", es5Template="es5TooltipFormat" %}

{% endtab %}

## Tooltip template

Any HTML element can be displayed in tooltip using the ‘template’ property. You can use `${datafield}` as placeholder in HTML element to display the values from data source.

The following example shows tooltip template.

{% tab template= "treemap/tooltip", es5Template="es5TooltipTemplate" %}

{% endtab %}