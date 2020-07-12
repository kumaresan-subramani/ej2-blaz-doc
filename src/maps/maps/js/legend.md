# Legend

A legend is a key used on a map that contains swatches of symbols with descriptions. It provides valuable information for interpreting what the map is displaying and can be represented in various colors, shapes or other identifiers based on the data. It gives a breakdown of what each symbol represents throughout the map.

## Visibility

The Legends can be made visible by setting the visible property of legendSettings to true.

## Positioning of the Legend

The legend can be positioned in two ways.

* Absolute Position.

* Dock Position.

### Absolute Position

Based on the margin values of X and Y-axes, the Map legends can be positioned with the support of `location.x` and `location.y` properties available in legendSettings. For positioning the legend based on margins corresponding to a map, position value is set as ‘Float’.

### Dock Position

The map legends can be positioned in following locations within the container.
You can set this option by using `position` property in legendSettings.

    1 Top

    2 Left

    3 Bottom

    4 Right

above four positions can be aligned combination of 'Near', 'Center' and 'Far' using `alignment` in `legendSettings`. So legend can be aligned 12 positions.

## Legend Mode

Legend had two type of mode. `Default` mode and `Interactive` mode.

### Default Mode

Default mode legends having symbols with legend labels, used to identify the shape or bubble or marker color.

### Interactive Mode

The legends can be made interactive with an arrow mark indicating the exact range color in the legend when the mouse hovers over the corresponding shapes. You can enable this option by setting `mode` property in legendSettings value as “Interactive” and default value of `mode` property is “Default” to enable the normal legend.

## Legend Size

The map legend size can be modified by using the `height` and `width` properties in `legendSettings`.

## Legend opacity

To specify the transparency for legend shape set `opacity` property in `legendSettings`.

## Legend for Shapes

The Layer shape type legends can be generated for each color mappings in shape settings.Assign for the layer `dataSource`. Provide the `shapePropertyPath` value as 'name and `shapeDataPath` value as 'State'.Finally set `legendSettings.visible` as true

To enable the equal colormapping refer the `shapeSettings.colorMapping` code snippet.

{% tab template= "maps/default-map", es5Template="legend" %}

{% endtab %}

## Legend Shape

To get the legend shape value for `legendSettings` by using `shape` property. You can customize the shape by using the `shapeWidth` and `shapeHeight` property.

## Legend for items excluded from color mapping

Based on the ranges in data source, get the excluded ranges from color mapping, and then show the legend with excluded range values are bound to the specific legend.Bind the `population_density` value to `dataSource` layer, and then specify the `colorValuePath` as 'density' to map the range values for shapes. Refer to the following the code example for more details.

{% tab template= "maps/default-map", es5Template="legend-shape" %}

{% endtab %}

## Hide desired legend items

To enable or disable the desired legend for each colormapping, set the `showLegend` property to `true` in `colorMapping`.

{% tab template= "maps/default-map", es5Template="hidedesiredlegend" %}

{% endtab %}

## Hide legend items based data source value

To enable or disable the legend visibility for each item, bind the field name in the data source to the `showLegendPath` property in `legendSettings`.

The following code example shows how to hide the legend items based data source value.

{% tab template= "maps/default-map", es5Template="hidedesiredlegendDS" %}

{% endtab %}

## Bind legend item text from data source

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

{% tab template= "maps/default-map", es5Template="bindlegendtext" %}

{% endtab %}

## Hide duplicate legend items

To enable or disable the duplicate legend items, set the property `removeDuplicateLegend` property to `true` in `legendSettings`.

{% tab template= "maps/default-map", es5Template="duplicatelegend" %}

{% endtab %}

Refer the [`API`](../api/maps/legendSettingsModel/) for Legend feature.