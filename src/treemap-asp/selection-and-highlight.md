# Selection and Highlight

## Selection

Selection is used to select a particular group or item to differentiate from other items. Each item or group can be selected and deselected when interacting with the items.

By tapping on the specific legend, the shapes which are bounded to the selected legend is also selected and vice versa.

The layer `selectionSettings.fill` property is used to change the selected item color. The `selectionSettings.border.color` and `selectionSettings.border.width` properties are used to customize the selected item's border.

The selection is enabled using the `selectionSettings.enable` property. To use selection feature in tree map, import the `TreeMapSelection`, and inject using the `TreeMap.Inject(TreeMapSelection);`.

Tree map selection is shown in the following example.

{% aspTab template="treemap/selection_highlight/selection", sourceFiles="selection.cs" %}

{% endaspTab %}

## Highlight

Hightlight is used to highlight an item or group from other items. Each item or group can be highlighted when hovering the mouse over items.

Hovering on the specific legend, the shapes which are bounded to the selected legend is also highlighted and vice versa.

The layer `highlightSettings.fill` property is used to change the highlighted item color. The `highlightSettings.border.color` and `highlightSettings.border.width` properties are used to customize the highlighted shape border. You can highlight an item by hovering the mouse over the item. The highlight is enabled using the `highlightSettings.enable` property.

The following code example shows highlighting the item.

{% aspTab template="treemap/selection_highlight/highlight", sourceFiles="highlight.cs" %}

{% endaspTab %}