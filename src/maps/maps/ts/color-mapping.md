# ColorMapping

ColorMapping used to customize the shape colors based on given values. It has three types: range color mapping, equal color mapping and desaturation color mapping.

## Range color mapping

Range color mapping is applied by the mapped value, which is numeric and with in the given color mapping ranges are provided in the `dataSource`. Refer the below dataSource for the population density of some countries.

```typescript
export let population_density = [
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

Bind the `population_density` value to layer `dataSource` and specify the `colorValuePath` as 'density' to map the range value for shapes. Refer the code snippet below.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "excludecolor" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { Population_Density } from './data.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        dataSource: Population_Density,
        shapeSettings: {
            colorValuePath: 'density',
            fill: '#E5E5E5',
            colorMapping: [
                {
                    from: 0.00001, to: 100, color: 'rgb(153,174,214)'
                },
                {
                    from: 100, to: 200, color: 'rgb(115,143,199)'
                },
                {
                    from: 200, to: 300, color: 'rgb(77,112,184)'
                },
                {
                    from: 300, to: 500, color: 'rgb(38,82,168)'
                },
                {
                    from: 500, to: 19000, color: 'rgb(0,51,153)'
                }
            ]
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Equal color mapping

Equal color mapping is used to apply color mapping if the mapped value is string. Following example demonstrate the permanent and non-permanent countries in the UN security council, in 2017. Refer the below dataSource.

```typescript
export let unCountries: object[] = [
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
];
```

Bind the unCountries data to the layer dataSource property and set the shapeSettings `colorValuePath` as 'Membership' and set the colorMapping values to that. Refer the below code snippet.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "equal" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { unCountries } from './data.ts';


let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'Country',
        shapePropertyPath: 'name',
        dataSource : unCountries,
        shapeSettings: {
            fill: '#E5E5E5',
            colorMapping: [
                {
                    value: 'Permanent',
                     color: '#C3E6ED'
                },
                {
                    color: '#F1931B',
                    value: 'Non-Permanent'
                }
            ],
            colorValuePath: 'Membership'
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Desaturation color mapping

Desaturation color mapping is used to apply colors to shapes with opacity based on given values for the `minOpacity` and `maxOpacity` properties in the map control.

The following code example shows how to apply desaturation color mapping to shapes.

```typescript
export let population_density = [
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

Bind the `population_density` value to layer `dataSource` layer,and then specify the `colorValuePath` as 'density' to map the range value for shapes. Refer the following code examples for more details.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "desaturation" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { Population_Density } from './data.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        dataSource: Population_Density,
        legendSettings:{
            visible: true
        },
        shapeSettings: {
            colorValuePath: 'density',
            colorMapping: [
                {
                    from: 0, to: 100, color: 'red', minOpacity:0.2, maxOpacity:1
                },
                {
                    from: 101, to: 200, color: 'blue', minOpacity:0.3, maxOpacity:1
                }
            ]
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Desaturation with multiple colors

Multiple colors are used to provide gradient effect to specific shapes based on the ranges in the datasource.

By using color property, you can set n number of colors.

The following code example shows how to use multiple colors.

```typescript
export let population_density = [
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

Bind the `population_density` value to layer `dataSource` and specify the `colorValuePath` as 'density' to map the range value for shapes. Refer to the following the code sample for more details.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "multiplecolors" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { Population_Density } from './data.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        dataSource: Population_Density,
        legendSettings:{
            visible: true
        },
        shapeSettings: {
            colorValuePath: 'density',
            colorMapping: [
                {
                    from: 0, to: 100, color: ['red','blue']
                },
                {
                    from: 101, to: 200, color: ['green','yellow']
                }
            ]
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Color for items excluded from color mapping

You will map the colors to the shapes based on the ranges or values in the data source records may have been excluded from the color mapping configuration, in which case you may also add the color for excluded items.

The following code example shows how to set the color for items excluded from color mapping.

```typescript
export let population_density = [
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

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "excludecolor" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { Population_Density } from './data.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'name',
        shapePropertyPath: 'name',
        dataSource: Population_Density,
        legendSettings:{
            visible: true
        },
        shapeSettings: {
            colorValuePath: 'density',
            colorMapping: [
                {
                    from: 0, to: 100, color: 'skyblue',
                },
                {
                    from: 101, to: 200, color: 'blue',
                },
                {
                    color: 'green'
                }
            ]
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

Refer the [`API`](../api/maps/colorMappingSettingsModel/) for Color Mapping feature.