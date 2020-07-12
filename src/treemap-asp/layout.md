# Layout

You can determine the visual representation of nodes belonging to all the tree map levels using the [`layoutType`] property. The available layout types are,

* Squarified
* SliceAndDiceVertical
* SliceAndDiceHorizontal
* SliceAndDiceAuto

## Squarified

Squarified layout displays the nested rectangles based on aspect ratio in tree map. The rectangles will be split based on height and width of parent. The default rendering type of layout is [`Squarified`].

{% aspTab template="treemap/layout/squarified", sourceFiles="squarified.cs" %}

{% endaspTab %}

## SliceAndDiceVertical

SliceAndDiceVertical layout creates rectangles with high aspect ratio and displays them sorted vertically.

{% aspTab template="treemap/layout/slice_vertical", sourceFiles="slice_vertical.cs" %}

{% endaspTab %}

## SliceAndDiceHorizontal

SliceAndDiceHorizontal layout creates rectangles with high aspect ratio and displays them sorted horizontally.

{% aspTab template="treemap/layout/slice_horizontal", sourceFiles="slice_horizontal.cs" %}

{% endaspTab %}

## SliceAndDiceAuto

SliceAndDiceAuto layout creates rectangles with high aspect ratio and displays them sorted both horizontally and vertically.

{% aspTab template="treemap/layout/slice_auto", sourceFiles="slice_auto.cs" %}

{% endaspTab %}

## Right-to-left rendering

The TreeMap control supports right-to-left rendering for all its elements such as nodes, tooltip, data labels, and legends.

## Legend with Rtl support

If you set the `enableRtl` property to true, then the legend icon will be rendered on the right and the legend text will be rendered on the left of the legend icon.

{% aspTab template="treemap/layout/legend-rtl", sourceFiles="legend-rtl.cs" %}

{% endaspTab %}

## Tooltip with Rtl support

If the `enableRtl` property is set to true, the tooltip data will be rendered in reverse direction.

The following example shows the format of the tooltip.

{% aspTab template="treemap/layout/tooltip-rtl", sourceFiles="tooltip-rtl.cs" %}

{% endaspTab %}

## Treemap Item Rendering Direction

By default, the direction of tree map item is `TopLeftBottomRight`. You can customize the rendering direction of the tree map item by setting the `renderDirection` property.
The TreeMap can be rendered in the following four different directions.
      `TopLeftBottomRight`
      `TopRightBottomLeft`
      `BottomRightTopLeft`
      `BottomLeftTopRight`

The following example demonstrate how to render the treemap in the RTL direction with `TopLeftBottomRight`.

{% aspTab template="treemap/layout/render-direction-one", sourceFiles="render-direction-one.cs" %}

{% endaspTab %}

The following example demonstrate how to render the treemap in the RTL direction with `TopRightBottomLeft`.

{% aspTab template="treemap/layout/render-direction-two", sourceFiles="render-direction-two.cs" %}

{% endaspTab %}

The following example demonstrate how to render the treemap in the RTL direction with `BottomRightTopLeft`.

{% aspTab template="treemap/layout/render-direction-three", sourceFiles="render-direction-three.cs" %}

{% endaspTab %}

The following example demonstrate how to render the treemap in the RTL direction with `BottomLeftTopRight`.

{% aspTab template="treemap/layout/render-direction-four", sourceFiles="render-direction-four.cs" %}

{% endaspTab %}