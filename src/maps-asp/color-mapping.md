# Color mapping

ColorMapping used to customize the shape colors based on given values. It has three types: range color mapping, equal color mapping and desaturation color mapping.

## Range color mapping

The range color mapping is used to apply color mapping if the mapped value is numeric and with in the given color mapping range that provided in the `dataSource`. Refer to the following dataSource for the population density of some countries.

```sh
 [
    ...
    {
        'code': 'AE',
        'value': 90,
        'name': 'United Arab Emirates',
        'population': 8264070,
        'density': 99
    },
    {
        'code': 'GB',
        'value': 257,
        'name': 'United Kingdom',
        'population': 62041708,
        'density': 255
    },
    {
        'code': 'US',
        'value': 34,
        'name': 'United States',
        'population': 325020000,
        'density': 33
    }
    ...
    ];
```

Bind the `populationData` value to layer `dataSource` and specify the `colorValuePath` to 'density' to map the range value for shapes. Refer to the following code sample.

{% aspTab template="maps/colormapping/colorvaluepath", sourceFiles="colorvaluepath.cs" %}

{% endaspTab %}

## Equal color mapping

Equal color mapping is used to apply the color mapping if the mapped value is string. The following example demonstrates the permanent and non-permanent countries in the UN security council, in 2017. Refer to the following dataSource.

```sh
[
{ Country: 'China', Membership: 'Permanent' },
{ Country: 'France', Membership: 'Permanent' },
{ Country: 'Russia', Membership: 'Permanent' },
{ Country: 'United Kingdom', Membership: 'Permanent' },
{ Country: 'United States', Membership: 'Permanent' },
{ Country: 'Bolivia', Membership: 'Non-Permanent' },
{ Country: 'Eq. Guinea', Membership: 'Non-Permanent' },
{ Country: 'Ethiopia', Membership: 'Non-Permanent' },
{ Country: "Côte d'Ivoire", Membership: 'Permanent' },
{ Country: 'Kazakhstan', Membership: 'Non-Permanent' },
{ Country: 'Kuwait', Membership: 'Non-Permanent' },
{ Country: 'Netherlands', Membership: 'Non-Permanent' },
{ Country: 'Peru', Membership: 'Non-Permanent' },
{ Country: 'Poland', Membership: 'Non-Permanent' },
{ Country: 'Sweden', Membership: 'Non-Permanent' },
]
```

Bind the unCountries data to the layer of the dataSource property and set the shapeSettings `colorValuePath` to 'Membership' and then set the colorMapping values to that. Refer to the following code sample.

{% aspTab template="maps/colormapping/equalcolormapping", sourceFiles="equalcolormapping.cs" %}

{% endaspTab %}

## Desaturation color mapping

Desaturation color mapping is used to apply colors with opacity to shapes based on the given values for the [`minOpacity`] and [`maxOpacity`] properties in the map control.

```sh
 [
    ...
    {
        'code': 'AE',
        'value': 90,
        'name': 'United Arab Emirates',
        'population': 8264070,
        'density': 99
    },
    {
        'code': 'GB',
        'value': 257,
        'name': 'United Kingdom',
        'population': 62041708,
        'density': 255
    },
    {
        'code': 'US',
        'value': 34,
        'name': 'United States',
        'population': 325020000,
        'density': 33
    }
    ...
    ];
```

Bind the `populationData` value to layer `dataSource` and specify the `colorValuePath` to 'density' to map the range value for shapes. Refer to the following code sample.

{% aspTab template="maps/colormapping/desaturationcolormapping", sourceFiles="desaturationcolormapping.cs" %}

{% endaspTab %}

## Desaturation with multiple colors

Multiple colors are used as gradient effect to the specific shapes based on the ranges in the datasource.

By using color API, you can set n number of colors.

The following code example shows how to use multiple colors.

```sh
 [
    ...
    {
        'code': 'AE',
        'value': 90,
        'name': 'United Arab Emirates',
        'population': 8264070,
        'density': 99
    },
    {
        'code': 'GB',
        'value': 257,
        'name': 'United Kingdom',
        'population': 62041708,
        'density': 255
    },
    {
        'code': 'US',
        'value': 34,
        'name': 'United States',
        'population': 325020000,
        'density': 33
    }
    ...
    ];
```

Bind the `populationData` value to layer `dataSource` and specify the `colorValuePath` to 'density' to map the range value for shapes. Refer to the following code sample.

{% aspTab template="maps/colormapping/desaturationwithmultiplecolors", sourceFiles="desaturationwithmultiplecolors.cs" %}

{% endaspTab %}

## Color for items excluded from color mapping

You will map the colors to the shapes based on the ranges or values in the data source records may have been excluded from the color mapping configuration, in which case you may also add the color for excluded items.

The following code example shows how to set the color for items excluded from color mapping.

```sh
 [
    ...
    {
        'code': 'AE',
        'value': 90,
        'name': 'United Arab Emirates',
        'population': 8264070,
        'density': 99
    },
    {
        'code': 'GB',
        'value': 257,
        'name': 'United Kingdom',
        'population': 62041708,
        'density': 255
    },
    {
        'code': 'US',
        'value': 34,
        'name': 'United States',
        'population': 325020000,
        'density': 33
    }
    ...
    ];
```

In following code example, You have added color mapping for the ranges from 0 to 200. If we have any records in the data source beyond this range, color mapping will not be applied. To apply the color for these excluded items, set `color` value in the `colorMapping` with out range or value.

{% aspTab template="maps/colormapping/excludedcolormapping", sourceFiles="excludedcolormapping.cs" %}

{% endaspTab %}

Refer the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsColorMapping.html) for Color Mapping feature.