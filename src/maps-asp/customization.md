# Customization

## customize shape

The following properties are available in `shapeSettings` property to customize the shapes of the Maps component.

* `fill` - Customizes the shape color.
* `autofill` - Applies the default palette colors to shapes.
* `palette` - Applies own custom palette for shapes.
* `border` - Customizes the maps shape border.
* `dashArray` - Customizes the different dash array border line format.
* `opacity` - Customizes the shape opacity.

{% aspTab template="maps/customization/fill", sourceFiles="fill.cs" %}

{% endaspTab %}

To apply default palette colors for shapes need to enable the `autofill` property.

{% aspTab template="maps/customization/autofill", sourceFiles="autofill.cs" %}

{% endaspTab %}

To apply own custom palette for shape, provide the palette colors for the `palette` property.

{% aspTab template="maps/customization/palette", sourceFiles="palette.cs" %}

{% endaspTab %}

Refer to `shapeSettings` [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsShapeSettings.html) for shape customization.
For more customization, see the [`colormapping`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsColorMapping.html) feature.

## Projection Type

By default, the maps are rendered by Mercator projection type. In this type, the maps are rendered based on coordinates, so it is not stretched.

The maps control has the following projection types:

* Mercator
* Equirectangular
* Miller
* Eckert3
* Eckert5
* Eckert6
* Winkel3
* AitOff.

{% aspTab template="maps/customization/projection", sourceFiles="projection.cs" %}

{% endaspTab %}