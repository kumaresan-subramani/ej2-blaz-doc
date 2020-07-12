# Customization

## customize shape

The following properties are available in `shapeSettings` property to customize the shapes of the Maps component.

* `fill` - Customizes the shape color.
* `autofill` - Applies the default palette colors to shapes.
* `palette` - Applies own custom palette for shapes.
* `border` - Customizes the maps shape border.
* `dashArray` - Customizes the different dash array border line format.
* `opacity` - Customizes the shape opacity.

```typescript
import { Maps } from '@syncfusion/ej2-maps';

let map: Maps = new Maps({
    layers: [{
        layerType: 'Geometry',
        shapeData: worldmap,
        shapeSettings: {
            fill: '#33CCFF',
            border: { color: '#FFFFFF', width: 2}
        }
    }]
});

map.appendTo('#element');
```

To apply the default palette colors for shapes, enable the `autofill` property.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "fill" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    layers: [{
        layerType: 'Geometry',
        shapeData: world_map,
        shapeSettings: {
            autofill: true
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

To apply own custom palette to shapes, provide the palette colors to  `palette`.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "auto-fill" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';


let map: Maps = new Maps({
    layers: [{
        layerType: 'Geometry',
        shapeData: world_map,
        shapeSettings: {
            autofill: true,
            palette: ['#33CCFF', '#FF0000', '#800000', '#FFFF00', '#808000']
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

Refer the `shapeSettings` [`API`](../api/maps/shapeSettingsModel/) for Shape Customization.
For more customization see [`colormapping`](../maps/color-mapping/) feature.

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

{% tab template= "maps/projection",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "projection" %}

```typescript
import { Maps, ProjectionType } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { projectionData } from './projection-data.ts';

let map: Maps = new Maps({
        projectioType: 'Mercator',
        layers: [
            {
                shapeData: world_map,
                shapeDataPath: 'Country',
                shapePropertyPath: 'name',
                dataSource: projectionData,
                tooltipSettings: {
                    visible: true,
                    valuePath: 'Country',
                },
                shapeSettings: {
                    fill: '#E5E5E5',
                    colorMapping: [
                        {
                            value: 'Permanent',
                            color: '#EDB46F'
                        },
                        {
                            color: '#F1931B',
                            value: 'Non-Permanent'
                        }
                    ],
                    colorValuePath: 'Membership'
                }
            }
        ]
});

map.appendTo('#container');
document.getElementById('projectiontype').onchange = function(){
      let ele: HTMLSelectElement = (<HTMLSelectElement>document.getElementById('projectiontype'))
      maps.projectionType = <ProjectionType>ele.value;
      maps.refresh();
}
```

{% endtab %}
