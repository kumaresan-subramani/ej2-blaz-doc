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

## Displaying layer in the view

In Maps, you can load multiple shape files. Using the `baseLayerIndex` property, you can select a layer to display on user interface.

In this example, we have loaded two layers with the World map and the United States map shape data and selected a layer using the `baseLayerIndex` property to show that layer on the web page.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "layerView" %}

```typescript
import { world_map } from './world-map.ts';
import { usa_map } from '../default-map-cs1/usa.ts';
import { Maps} from '@syncfusion/ej2-maps';
let map: Maps = new Maps({
   baseLayerIndex: 1,
   layers: [
   {
       shapeData: world_map,
   }, {
       shapeData: usa_map
   }]
});
map.appendTo('#element');
```

{% endtab %}

If you set the `baseLayerIndex` value to 0, the world map will be loaded.

This concept is used in the Maps drill-down feature, so the corresponding shape will be loaded when clicking a shape of the maps.

Refer the [`API`](../api/maps/layerSettingsModel/) for Layers feature.

## See Also

* [Adding multiple layers in map](../maps/how-to/multiple-layer)
* [Display geometry shape in bing maps](../maps/how-to/bing-map)
* [Custom path map](../maps/how-to/custom-path)