# ColorMapping

ColorMapping used to customize the shape colors based given values. It has two types, one range color mapping and equal color mapping.

## Range color mapping

Range color mapping applied by the mapped value is numeric and with in the given color mapping ranges provided in the `dataSource`.Bind the `population_density` value to layer `dataSource` and specify the `colorValuePath` as 'density' to map the range value for shapes. Refer the code snippet below.

{% tab template="maps/default-map", es5Template="excludecolor" %}

{% endtab %}

## Equal color mapping

Equal color mapping used to apply color mapping if the mapped value is string. Following example demonstrate the permanent and non-permanent countries in the UN security council, in 2017. Refer the below dataSource.
Bind the unCountries data to the layer dataSource property and set the shapeSettings `colorValuePath` as 'Membership' and set the colorMapping values to that. Refer the below code snippet.

{% tab template="maps/default-map", es5Template="equal" %}

{% endtab %}

## Desaturation color mapping

Desaturation color mapping is used to apply colors with opacity to shapes based on the given values for the [`minOpacity`] and [`maxOpacity`] properties in the map control.Bind the `population_density` value to layer `dataSource` layer,and then specify the `colorValuePath` as 'density' to map the range value for shapes. Refer the following code examples for more details.

{% tab template="maps/default-map", es5Template="desaturation" %}

{% endtab %}

## Desaturation with multiple colors

Multiple colors are used as gradient effect to the specific shapes based on the ranges in the datasource.

By using color API, you can set n number of colors.Bind the `population_density` value to layer `dataSource` and specify the `colorValuePath` as 'density' to map the range value for shapes. Refer to the following the code sample for more details.

{% tab template="maps/default-map", es5Template="multiplecolors" %}

{% endtab %}

## Color for items excluded from color mapping

You will map the colors to the shapes based on the ranges or values in the data source records may have been excluded from the color mapping configuration, in which case you may also add the color for excluded items. In following code example, You have added color mapping for the ranges from 0 to 200. If we have any records in the data source beyond this range, color mapping will not be applied. To apply the color for these excluded items, set `color` value in the `colorMapping` with out range or value.

{% tab template="maps/default-map", es5Template="excludescolor" %}

{% endtab %}

Refer the [`API`](../api/maps/colorMappingSettingsModel/) for Color Mapping feature.