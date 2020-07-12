# OpenStreetMap

The OpenStreetMap (OSM) is the world map built by a community of developers; it is free to use under an open license. It allows you to view geographical data in a collaborative way from anywhere on the earth. The OSM map provides small tile images to display the map area in the Maps component.

## Add OpenStreetMap

One of the most important features in EJ2 Maps component is the built-in online map provider support. By using this feature, you can render OpenStreetMap in the maps component. This provides the ability to visualize street map tiles without using any external shape files.

You can enable this feature by setting the value of `layerType` property to `OSM`

{% tab template= "maps/Providers",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "OSM" %}

```typescript

import { Maps } from '@syncfusion/ej2-maps';
let map: Maps = new Maps({
    layers: [
        {
            layerType: "OSM"
        }
    ]
}, '#element');

```

{% endtab %}

## Zooming and panning

You can zoom and pan the OSM maps layer. Zooming helps you get a closer look at a particular area on a map for in-depth analysis. Panning helps you to move a map around to focus the targeted area.

{% tab template= "maps/Providers",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "OSMZoom" %}

```typescript
import { Maps , Zoom} from '@syncfusion/ej2-maps';
Maps.Inject(Zoom);
let map: Maps = new Maps({
    zoomSettings: {
        enable: true,
        toolBars: ["Zoom", "ZoomIn", "ZoomOut", "Pan", "Reset"]
    },
    layers: [
        {
            layerType: "OSM"
        }
    ]
}, '#element');

```

{% endtab %}

## Adding markers and navigation line

Markers can be added to the layers of OSM maps by setting the corresponding location's coordinates of latitude and longitude using `markerSettings` property. You can add navigation lines on top of an OSM maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the `navigationLineSettings` property.

{% tab template= "maps/Providers",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "OSMMarkers" %}

```typescript

import { Maps, NavigationLine, Marker } from '@syncfusion/ej2-maps';
Maps.Inject(NavigationLine, Marker);
let map: Maps = new Maps({
    zoomSettings: {
        zoomFactor: 4
    },
    centerPosition: {
        latitude: 29.394708,
        longitude: -94.954653
    },
    layers: [
        {
            layerType: "OSM",
            markerSettings: [{
                visible: true,
                height: 25,
                width: 15,
                dataSource: [
                    {
                        latitude: 34.060620,
                        longitude: -118.330491,
                        name: "California"
                    },
                    {
                        latitude: 40.724546,
                        longitude: -73.850344,
                        name: "New York"
                    }
                ]
            }],
            navigationLineSettings: [{
                visible: true,
                color: "blue",
                width: 5,
                angle: 0.1,
                latitude: [34.060620, 40.724546],
                longitude: [-118.330491,-73.850344]
            }]
        }
    ]
}, '#element');

```

{% endtab %}

## Sublayer

You can render any GeoJSON shape as a sublayer on top of an OSM maps layer for highlighting a particular continent or country in OSM maps by adding another layer and specifying the type to SubLayer.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html", es5Template="OSMSublayer" %}

```typescript

import { Maps } from '@syncfusion/ej2-maps';
import { Africa_Continent } from './Africa_Continent.ts';
let map: Maps = new Maps({
    layers: [
        {
            layerType: "OSM"
        },
        {
            shapeData: Africa_Continent,
            type: 'SubLayer',
            shapeSettings: {
                fill: "blue"
            }
        }
    ]
}, '#element');

```

{% endtab %}
