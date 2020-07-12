# Markers

Markers are notes that are used to leave a message on the map. It indicates or marks a specific location with desired symbols on the maps.

The `dataSource` property has a list of objects that contains data for markers. By default, it displays the bound data at the specified latitude and longitude. Using the `visible` API, you can enable or disable the markers.

There are two ways to set marker for map.

* Marker and marker template

* Adding marker objects to map.

## Marker and marker template

The `markerSettings.dataSource` property has a list of objects that contains the data for Annotation. By default, it displays the bound data at the specified latitude and longitude. The `markerSettings.template` property is used for customizing the template for markers.

**Note:** markerSettings is an Array property.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "marker" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        markerSettings: [
            {
                        visible: true,
                        template: '<div id="marker4" class="markerTemplate">Europe' +
                            '</div>',
                        dataSource: [
                            { latitude: 49.95121990866204, longitude: 18.468749999999998 }
                        ],
                        animationDuration: 0,
                    },
                    {
                        visible: true,
                        template: '<div id="marker5" class="markerTemplate" style="width:50px">North America' +
                            '</div>',
                        dataSource: [
                            { latitude: 59.88893689676585, longitude: -109.3359375 }
                        ],
                        animationDuration: 0
                    },
                    {
                        visible: true,
                        template: '<div id="marker6" class="markerTemplate" style="width:50px">South America' +
                            '</div>',
                        dataSource: [
                            { latitude: -6.64607562172573, longitude: -55.54687499999999 }
                        ],
                        animationDuration: 0
                    },

            }
        ]
    }]
});
map.appendTo('#element');
```

{% endtab %}

```html
<div  id="template" style="display: none;">
    <div>
        <div  style="background-image:url(http://js.syncfusion.com/demos/web/Images/map/pin.png)margin-left:3px;height:40px;width:25px;margin-top:-15px;">
        </div>
    </div>
</div>
```

## Adding marker objects to map

The n number of markers can be added to shape layers with `markerSettings.dataSource` property. Each dataSource object contains the following list of properties.

* label - Text that displays some information about the annotation in text format.
* latitude - Latitude point determine the Y-axis position of annotation.
* longitude - Longitude point determine the X-axis position of annotation.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "marker-object" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        markerSettings: [
            {
                visible: true,
                template: '<div> {{:city}}<div>',
                dataSource: [
                    { latitude: 37.0000, longitude: -120.0000, city: 'California' },
                    { latitude: 40.7127, longitude: -74.0059, city: 'New York' },
                    { latitude: 42, longitude: -93, city: 'Iowa' }
                ]
            }
        ]
    }]
});
map.appendTo('#element');
```

{% endtab %}

```html
<div  id="template" style="display: none;">
        <div>
            <div style="margin-left:8px;height:45px;width:120px;margin-top:-23px;">
                <label style="color:black;margin-left:15px;font-weight:normal;">\{\{\:city\}\}</label>
             </div>
         </div>
    </div>
```

## Marker shapes

The Maps component contains the following marker shapes. You can select any shape using the `shape` property in `markerSettings`.

* Ballon
* Circle
* Cross
* Diamond
* Image
* Rectangle
* Start
* Triangle
* VerticalLine
* HorizontalLine

## Multiple marker groups

You can specify multiple marker groups and customize each group of markers separately as demonstrated in the following example.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "markerColorDataSource" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        markerSettings: [{
            visible: true,
            shape: 'Diamond',
            height: 15,
            fill: "green",
            width: 15,
            dataSource: [
                {
                    latitude: 37.0000, longitude: -120.0000, name:'California',
                },
                {
                    latitude: 40.7127, longitude: -74.0059, name:"New York"
                },
                {
                    latitude: 42, longitude: -93, name:'Iowa'
                }
            ]
        },
        {
            visible: true,
            dataSource: [{
                latitude: 19.228825, longitude: 72.854118, name: "Mumbai"
            }, {
                latitude: 28.610001, longitude: 77.230003, name: "Delhi"
            }, {
                latitude: 13.067439, longitude: 80.237617, name: "Chennai"
            }],
            shape: 'Circle',
            fill: "blue",
            height: 10,
            width: 10
        }],
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Customize marker shapes from data source

### Bind different colors and shapes to the marker from data source

The location on the map is marked by different marker shapes using `shapeValuePath` property in `markerSettings`. Based on the field name in the data source bind the value to the `shapeValuePath` property. Also, you can customize the marker shape color by binding the color value field name in the data source to the `colorValuePath` property in `markerSettings`.

A default marker object is represented by `balloon` shape. You can set various shapes to the marker object by using `shape` property in `markerSettings`. Also, you can change the shapes of the marker from the datasource.

The following shapes are used for the marker object.
* Circle
* Rectangle
* Balloon
* Cross
* Polyline
* Diamond
* Star
* Triangle
* HorizontalLine
* VerticalLine
* pentagon

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "markerColorDataSource" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        markerSettings: [{
            visible: true,
            shapeValuePath:'shape',
            colorValuePath:'color',
            dataSource: [
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe', color:'red', shape:'Triangle' },
                { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America',
                color:'blue', shape:'Pentagon' },
                { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America',
                color:'green', shape:'InvertedTriangle' }
            ]
        }],
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Marker Zooming

The map is initially scaled to the center value based on the marker distance. This can be achieved by setting `shouldZoomInitially` property in `zoomSettings` as `true`.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "markerZooming" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker, Zoom} from '@syncfusion/ej2-maps';
Maps.Inject(Marker, Zoom);
let map: Maps = new Maps({
    zoomSettings: {
        enable: true,
        horizontalAlignment:'Near',
        shouldZoomInitially: true
    },
    layers: [{
        shapeData: world_map,
        markerSettings: [{
            visible: true,
            dataSource: [
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America' },
                { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America'}
                ]
            }],
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Marker Cluster Expand

The cluster is formed by grouping an identical and non-identical marker from the surrounding area. By clicking on the cluster and setting `allowClusterExpand` property in `markerClusterSettings` as `true` to expand the identical markers. If you zoom in any of the locations of the cluster, the number on the cluster will decrease and the overlapping marker will be split into an individual marker on the map. When you zoom out, it will increase the marker count and then cluster it again.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "markerClusterExpand" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker, Zoom} from '@syncfusion/ej2-maps';
Maps.Inject(Marker, Zoom);
let map: Maps = new Maps({
    zoomSettings: {
        enable: true,
        mouseWheelZoom : true,
    },
    layers: [{
        shapeData: world_map,
        markerClusterSettings: {
            allowClustering: true,
            allowClusterExpand: true,
            shape: 'Circle',
            height: 40,
            width: 40,
            labelStyle : { color: 'white'},
        },
        markerSettings: [{
            visible: true,
            dataSource: [
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America' },
                { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America'}
            ]
        }],
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Enable the Legend for map markers

Legend can be enabled for marker using `legendSettings.type` as **Markers** and legend visible as true, need to inject Legend module to Maps using the `Maps.Inject(Legend)`. Refer the code snippet to enable the legend for the markers.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "marker-object" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker, Legend} from '@syncfusion/ej2-maps';
Maps.Inject(Marker, Legend);
let map: Maps = new Maps({
    legendSettings: {
        visible: true,
        type: 'Markers'
    },
    layers: [{
        shapeData: world_map,
        markerSettings: [
            {
               visible: true,
               legendText: 'city',
                dataSource: [
                    { latitude: 37.0000, longitude: -120.0000, city: 'California' },
                    { latitude: 40.7127, longitude: -74.0059, city: 'New York' },
                    { latitude: 42, longitude: -93, city: 'Iowa' }
                ]
            }
        ]
    }]
});
map.appendTo('#element');
```

{% endtab %}

## Marker Clustering

Maps provides support to hide and cluster markers when they overlap each other.

The number on a cluster indicates how many overlapped markers it contains. If you zoom any of the cluster locations, the number on the cluster will decrease and you will begin to see the individual markers on the map. When zooming out, the overlapping marker will increase so that you can cluster it again and increase the count over the cluster.

Using the [`markerClusterSettings.allowClustering`](../api/maps/markerClusterSettings/#allowclustering) API, you can enable or disable this cluster support. The [`markerClusterSettings`](../api/maps/markerClusterSettings) API also helps to customize clusters.

The [`MarkerClusterRendering`](../api/maps/iMarkerClusterRenderingEventArgs) event occurs when each cluster is rendered. You can also use this to customize the cluster. The [`markerClusterClick`](../api/maps/iMarkerClickEventArgs) and [`markerClusterMouseMove`](../api/maps/iMarkerClusterMoveEventArgs) events on mouse move and on clicking the cluster.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html", es5Template="cluster" %}

```typescript
import { world_map } from './world-map.ts';
import { cluster } from './cluster.ts'
import { Maps , Marker,MapsTooltip, MarkerSettings } from '@syncfusion/ej2-maps';
Maps.Inject(Marker,MapsTooltip);
// initialize Maps component
let map: Maps = new Maps({
    useGroupingSeparator: true,
        format: 'n',
        zoomSettings: {
            enable: true
        },
        titleSettings: {
            text: 'Top 13 largest cities in the World',
            textStyle: {
                size: '16px'
            }
        },
        layers: [
            {
                shapeData: world_map,
                shapeSettings: {
                    fill: '#C1DFF5'
                },
                markerClusterSettings: {
                    allowClustering: true,
                    shape: 'Circle',
                    height: 40,
                    width: 40,
                    labelStyle : { color: 'white'},
                },
                markerSettings: [
                    {
                        visible: true,
                        dataSource: cluster,
                        shape: 'Balloon',
                        tooltipSettings: {
                            format: 'City: ${city} <br> Area: ${area}',
                            visible: true,
                            valuePath: 'area',
                        },
                        height: 20,
                        width: 20,
                        animationDuration: 0
                    },

                ]
            }
        ]
}, '#element');
```

{% endtab %}

Refer the [`API`](../api/maps/markerSettingsModel/) for Marker feature.

## See Also

* [Add different types of markers](../maps/how-to/marker-type)
* [Tooltip for marker](../maps/how-to/marker-type)