# User Interactions

Options like zooming, panning, single click and double click, highlight and map selection enables the effective interaction on Map elements.

## Zooming

The zooming feature enables you to zoom in and zoom out a map to show in-depth information. It is controlled by using the `zoomFactor` property of the `zoomSettings`. When the zoomFactor is increased, the map is zoomed in. When the zoomFactor is decreased, the map is zoomed out.

### Enable zooming

To enable the zooming feature, set the `zoomSettings.enable` to true in maps.

### Enable panning

To enable the panning feature, set the [`EnablePanning`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsZoomSettings~EnablePanning.html) property of [`zoomSettings`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsZoomSettings.html) to **true**.

{% aspTab template="maps/user-interactions/panning", sourceFiles="panning.cs" %}

{% endaspTab %}

### Various type of zooming

Zooming can be performed in following types:

<b>Zooming toolbar</b>

By default, the toolbar is rendered with `zoom-in`, `zoom-out`, and `reset` options when it is set to 'true' in the `enable` property of `zoomSettings`. You can also customize the toolbar items using the `toolBArs` property in `zoomSettings`.

The following options are available in toolbar, and you can use the options as needed:

1. Zoom - Provides rectangular zoom support.
2. ZoomIn - Zooms in the maps.
3. ZoomOut - Zooms out the maps.
4. Pan - Switches to panning if rectangular zoom is activated.
5. Reset - Restores the maps to the default view.

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsZoomSettings.html) links for zooming.

{% aspTab template="maps/user-interactions/zoom", sourceFiles="zoom.cs" %}

{% endaspTab %}

<b>Pinch Zooming</b>

Use the `pinchZooming` property in `zoomSettings` to enable or disable the pinch zooming.

{% aspTab template="maps/user-interactions/pinchzoom", sourceFiles="pinchzoom.cs" %}

{% endaspTab %}

<b>Single-click zooming</b>

Use the `zoomOnClick` property in `zoomSettings` to enable or disable the single-click zooming

{% aspTab template="maps/user-interactions/singleclickzoom", sourceFiles="singleclick.cs" %}

{% endaspTab %}

<b>Double-click zooming</b>

Use the `doubleClickZoom` property in `zoomSettings` to enable or disable the double-click zooming.

{% aspTab template="maps/user-interactions/doubleclickzoom", sourceFiles="doubleclick.cs" %}

{% endaspTab %}

<b>Mouse wheel zooming</b>

Use the `mouseWheelZoom` property in `zoomSettings` to enable or disable mouse wheel zooming.

{% aspTab template="maps/user-interactions/mousewheel", sourceFiles="mousewheel.cs" %}

{% endaspTab %}

### Zooming with animation

You can use the `animationDuration` property in  `layers` property to zoom in or zoom out the maps with animation.

{% aspTab template="maps/user-interactions/animationzoom", sourceFiles="animationzoom.cs" %}

{% endaspTab %}

## Selection

Each shape in a map can be selected and deselected while interacting with the shapes.

The `selectionSettings.fill` property is used to change the selected layer shape's color. The `selectionSettings.border.color` and `selectionSettings.border.width` properties are used to customize the selected shape's border.

You can select a shape by tapping the shape. The single selection is enabled by using the `selectionSettings.enable` property of shape layer. When the `selectionSettings.enable` is set to false, the shapes cannot be selected.

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsSelectionSettings.html) and code snippet for selection.

{% aspTab template="maps/user-interactions/selection", sourceFiles="selection.cs" %}

{% endaspTab %}

## Initial shape selection

Initially, the shape can be selected by using the property `initialShapeSelection` and the values are mapped to the `shapePath` and `shapeValue`.

**Note:** initialShapeSelection is an Array property.

{% aspTab template="maps/user-interactions/initial-shape", sourceFiles="initial-shape.cs" %}

{% endaspTab %}

## Highlight

Each shape in a map can be highlighted while hovering the mouse over the shapes.

The `highlightSettings.fill` property is used to change the highlighted layer shape's color. The `highlightSettings.border.color` and `highlightSettings.border.width` properties are used to customize the highlighted shape's border.

You can highlight the a by hovering the mouse over the shape. The highlight is enabled by using the `highlightSettings.enable` property of shape layer. When the `highlightSettings.enable` property is set to false, the shapes cannot be highlighted.

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsHighlightSettings.html) and code snippet for highlight.

{% aspTab template="maps/user-interactions/highlight", sourceFiles="highlight.cs" %}

{% endaspTab %}

## Tooltip

Tooltip is used to show more information about a layer, bubble or marker on mouse over or touch end event performing.

Tooltip can be enabled separately for layer, bubble or marker by setting the `tooltipSettings.visible` to **true**. Tooltip's `valuePath` value needs to be set to display the dataSource, which field is tooltip text.

The following code snippet illustrates the tooltip that is enabled for layer to show shape data name field.

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsTooltipSettings.html) for tooltip feature.

{% aspTab template="maps/user-interactions/tooltip", sourceFiles="tooltip.cs" %}

{% endaspTab %}
