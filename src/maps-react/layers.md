# Layers

Map is maintained through `layers` and it can accommodate one or more layers.

## Multilayer

The Multilayer support allows you to load multiple shape files in a single container, enabling maps to display more information.

### Adding Multiple Layers in the Map

The shape layers is the core layer of the map. The multiple layers can be added in the shape layer `type` as `SubLayer`.

## SubLayer

In this example, World Map shape is used as shape data by utilizing the `“WorldMap.json”` file in the
following folder structure obtained from downloaded Maps_GeoJSON folder.

..\ Maps_GeoJSON\

You can assign the complete contents in `WorldMap.json` file to new JSON object. For better understanding, a
TS file `WorldMap.ts` is already created to store JSON data in JSON object “world_map” and also copy the
WorldMap.json file data, bind value to “usMap” like “world_map”.

`[WorldMap.ts]`

{% tab compileJsx=true%}

```tsx
export let worldmap = //Paste all the content copied from the JSON file//
```

{% endtab %}

`[usa.ts]`

{% tab compileJsx=true%}

```tsx
export let world_map = //Paste all the content copied from the WorldMap.JSON file//
```

{% endtab %}

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
//tslint:disable
import { world_map } from 'world-map.ts';
import { usa_map } from 'usa.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                        shapeSettings={ {
                            fill: '#9CBF4E',
                            border: { width: 0.5, color: 'White' },
                        } } />
                    <LayerDirective shapeData={usa_map} type="SubLayer"
                        shapeSettings={ {
                            fill: 'orange',
                            border: { width: 1, color: 'White' },
                        } } />
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Displaying layer in the view

In Maps,you can load multiple shape files. Using the `baseLayerIndex` property, you can select a layer to display on user interface.

In this examples, we have loaded two layers with the World map and the United States map shape data and selected a layer using the `baseLayerIndex` property to show that layer on the web page.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
//tslint:disable
import { world_map } from 'world-map.ts';
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" baseLayerIndex={1}>
                <LayersDirective>
                    <LayerDirective shapeData={world_map} />
                    <LayerDirective shapeData={usa_map} />
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

If you set the `baseLayerIndex` value to 0, the world map will be loaded.

This concept is used in the Maps drill-down feature, so the corresponding shape will be loaded when clicking a shape of the maps.

Refer the [`API`](../api/maps/layerSettingsModel/) for Layers feature.