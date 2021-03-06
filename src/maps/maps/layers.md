# Layers

Map is maintained through `layers` and it can accommodate one or more layers.

## Multilayer

The Multilayer support allows you to load multiple shape files in a single container, enabling maps to display more information.

### Adding Multiple Layers in the Map

The shape layers is the core layer of the map. The multiple layers can be added in the shape layers as `subLayers` within the shape layers.

## SubLayer

The subLayer is the collection of shape layers.

In this example, World Map shape is used as shape data by utilizing the `USA.json”` file in the following folder structure obtained from downloaded Maps_GeoJSON folder.

..\ Maps_GeoJSON\

You can assign the complete contents in `USA.json` file to new JSON object. For better understanding, a TS file `USA.ts` is already created to store JSON data in JSON object usa_map and also copy the USA.json file data, bind value to “california” like “world_map”.

`[WorldMap.ts]`

```typescript
export let world_map = //Paste all the content copied from the JSON file//
```

`[usa.ts]`

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "multiple-layer" %}

```typescript
import { usa_map } from './usa.ts';
import { california } from './california.ts';
import { texas } from './texas.ts';
import { Maps } from '@syncfusion/ej2-maps';

// initialize Maps component
let map: Maps = new Maps({
        layers: [
        {
            shapeData: usa_map,
            shapeSettings: {
                fill: '#E5E5E5',
                border: {
                    color: 'black',
                    width: 0.1
                }
            }
        },
        {
            shapeData: texas,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        },
        {
            shapeData: california,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        }
    ]
}, '#element');
```

{% endtab %}

Refer the [`API`](../api/maps/layerSettingsModel/) for Layers feature.

## See Also

* [Adding multiple layers in map](../maps/how-to/multiple-layer)
* [Display geometry shape in bing maps](../maps/how-to/bing-map)
* [Custom path map](../maps/how-to/custom-path)