# Color Mapping

Color mapping is used to customize each group or item colors based on specified types of color mappings.

The following options are available to customize the group and leaf items in the tree map control.

## Range color mapping

Range color mapping is used to apply color to items by giving specific ranges in the dataSource. You should specify the datasource field in the [`rangeColorValuePath`] property.

The following code example shows applying range color mapping.

{% aspTab template="treemap/colormapping/range", sourceFiles="range.cs" %}

{% endaspTab %}

## Equal color mapping

Equal color mapping is used to fill colors to each item by specifying equal value present in the datasource field that can be specified in the [`equalColorValuePath`] property.

The following code example shows applying equal color mapping.

{% aspTab template="treemap/colormapping/equal", sourceFiles="equal.cs" %}

{% endaspTab %}

## Desaturation color mapping

Desaturation color mapping is used to apply colors with opacity to items based on the given values for the [`minOpacity`] and [`maxOpacity`] properties in the tree map control.

The following code example shows applying desaturation color mapping.

{% aspTab template="treemap/colormapping/desaturation", sourceFiles="desaturation.cs" %}

{% endaspTab %}

## Palette color mapping

Palette color mapping is used to fill the same color to each group or leaf node by given colors in the [`palette`] property in tree map control.

The following code example shows applying  palette color mapping.

{% aspTab template="treemap/colormapping/pallete", sourceFiles="pallete.cs" %}

{% endaspTab %}

## Desaturation with multiple colors

Multiple colors are used as gradient effect to specific shapes based on the ranges in datasource.

By using color API, you can set n number of colors.

{% aspTab template="treemap/colormapping/pallete", sourceFiles="pallete.cs" %}

{% endaspTab %}

## Color for items excluded from color mapping

Based on the ranges in the data source, get the excluded ranges from color mapping, and then apply specific color to the items.

{% aspTab template="treemap/colormapping/excludecolor", sourceFiles="excludecolor.cs" %}

{% endaspTab %}

## Bind the colors to the items from data source

To set color for each items in treemap, bind the field name in the data source to the `rangeColorValuePath`.

{% aspTab template="treemap/colormapping/multiplecolor", sourceFiles="multiplecolor.cs" %}

{% endaspTab %}