# Markers

Markers are notes used to leave some message on the Maps component. It indicates or marks a specific location with desired symbols on the maps.

There are two ways to set marker for map.

* Marker and marker template

* Adding marker objects to map.

## Marker and marker template

The `markerSettings.dataSource` property has a list of objects that contains the data for Annotation.
By default, it displays the bound data at the specified latitude and longitude. The `markerSettings.template`
property is used for customizing the template for markers.

**Note:** markerSettings is an Array property. So we need to use Directives.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps">
                <Inject services={[Marker]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map}>
                        <MarkersDirective>
                                        <MarkerDirective visible={true}
                                            height={30}
                                            width={30}
                                            template='<div id="marker1">Europe</div>'
                                            dataSource={[{ latitude: 49.95121990866204, longitude: 18.468749999999998 }]}
                                        >
                                        </MarkerDirective>
                                        <MarkerDirective visible={true}
                                            height={30}
                                            width={30}
                                            template='<div id="marker2">North America</div>'
                                            dataSource={[{ latitude: 59.88893689676585, longitude: -109.3359375 }]}
                                        >
                                        </MarkerDirective>
                                        <MarkerDirective visible={true}
                                            height={30}
                                            width={30}
                                            template='<div id="marker3">South America</div>'
                                            dataSource={[{ latitude: -6.64607562172573, longitude: -55.54687499999999 }]}
                                        >
                                        </MarkerDirective>
                                        </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Adding marker objects to map

n number of markers can be added to shape layers with `markerSettings.dataSource` property. Each dataSource
object contains the following list of properties.

label - Text that displays some information about the annotation in text format.
latitude - Latitude point determine the Y-axis position of annotation.
longitude - Longitude point determine the X-axis position of annotation.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps">
                <Inject services={[Marker]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map}>
                        <MarkersDirective>
                        <MarkerDirective visible={true}
                                            shape= {'Circle'}
                                            dataSource={[{ latitude: 37.6276571, longitude: -122.4276688, name: 'San Bruno' }]}
                                        >
                                        </MarkerDirective>
                                        <MarkerDirective visible={true}
                                            height={30}
                                            width={30}
                                            template='<div id="marker1">Europe</div>'
                                            dataSource={[{ latitude: 49.95121990866204, longitude: 18.468749999999998 }]}
                                        >
                                        </MarkerDirective>
                                        <MarkerDirective visible={true}
                                            height={30}
                                            width={30}
                                            template='<div id="marker2">North America</div>'
                                            dataSource={[{ latitude: 59.88893689676585, longitude: -109.3359375 }]}
                                        >
                                        </MarkerDirective>
                                        <MarkerDirective visible={true}
                                            height={30}
                                            width={30}
                                            template='<div id="marker3">South America</div>'
                                            dataSource={[{ latitude: -6.64607562172573, longitude: -55.54687499999999 }]}
                                        >
                                        </MarkerDirective>
                                        </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
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

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps">
                <Inject services={[Marker]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map}>
                        <MarkersDirective>
                        <MarkerDirective visible={true}
                                            shape= {'Circle'} shapeValuePath= {'shape'} colorValuePath= {'color'}
                                            dataSource={[
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe', color:'red', shape:'Triangle' },
                                                { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America',
                                                color:'blue', shape:'Pentagon' },
                                                { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America',
                                                color:'green', shape:'InvertedTriangle' }
                                                ]}
                                        >
                                        </MarkerDirective>
                                        </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Marker Zooming

The map is initially scaled to the center value based on the marker distance. This can be achieved by setting `shouldZoomInitially` property in `zoomSettings` as `true`.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject, Zoom } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps" zoomSettings= {{enable: true, horizontalAlignment:'Near', shouldZoomInitially: true}}>
                <Inject services={[Marker, Zoom]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map}>
                        <MarkersDirective>
                        <MarkerDirective visible={true}
                                            shape= {'Circle'}
                                            dataSource={[
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America' },
                                                { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America'}
                                                ]}
                                        >
                                        </MarkerDirective>
                                        </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Marker Cluster Expand

The cluster is formed by grouping an identical and non-identical marker from the surrounding area. By clicking on the cluster and setting `allowClusterExpand` property in `markerClusterSettings` as `true` to expand the identical markers. If you zoom in any of the locations of the cluster, the number on the cluster will decrease and the overlapping marker will be split into an individual marker on the map. When you zoom out, it will increase the marker count and then cluster it again.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject, Zoom } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps" zoomSettings= {{enable: true, mouseWheelZoom : true }}>
                    <Inject services={[Marker, Zoom]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map} markerClusterSettings={{ allowClustering: true,  allowClusterExpand: true,shape: 'Circle', height: 40, width: 40, labelStyle: { color: 'white' }, }}>
                            <MarkersDirective>
                                <MarkerDirective visible={true} dataSource={[
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 49.95121990866204, longitude: 18.468749999999998, name:'Europe' },
                                                { latitude: 59.88893689676585, longitude: -109.3359375, name:'North America' },
                                                { latitude: -6.64607562172573, longitude: -55.54687499999999, name:'South America'}
                                                ]}  animationDuration={0}>
                                </MarkerDirective>
                            </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Enable the Legend for map markers

Legend can be enabled for marker using `legendSettings.type` as **Markers** and legend visible as true, need
to inject Legend module to Maps using the `Inject` tag. Refer the code snippet to enable the legend for the markers.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps" legendSettings={ { visible: true, type: 'Markers' } }>
                <Inject services={[Marker, Legend]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map}>
                        <MarkersDirective>
                        <MarkerDirective visible={true}
                                            legendText={ 'name'}
                                            shape= {'Circle'}
                                            dataSource={[{ latitude: 37.6276571, longitude: -122.4276688, name: 'San Bruno' },{ latitude: 33.5302186, longitude: -117.7418381, name: 'Laguna Niguel' },{ latitude: 40.7424509, longitude: -74.0081468, name: 'New York' }]}
                                        >
                                        </MarkerDirective>
                                        </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Marker Clustering

Maps provides support to hide and cluster marker when they overlap each other. The number on a cluster indicates how many overlapped markers it contains. If you zoom any of the cluster locations, the number on the cluster will decrease and you will begin to see the individual markers on the map. When zooming out, the overlapping marker will increase so that you can cluster it again and increase the count over the cluster.

Using the `markerClusterSettings.allowClustering` API, you can enable or disable this cluster support. The `markerClusterSettings` API also helps to customize clusters.

The `MarkerClusterRendering` event occurs when each cluster is rendered. You can also use this to customize the cluster. The `markerClusterClick` and `markerClusterMouseMove` events on mouse move and on clicking the cluster.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { cluster } from 'marker-cluster.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective, Marker, Inject, MapsTooltip, Zoom, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
                <MapsComponent id="maps" useGroupingSeparator={true} format='n' zoomSettings={{ enable: true  }} titleSettings={{ text: 'Top 13 largest cities in the World', textStyle: { size: '16px' } }}>
                    <Inject services={[Marker, MapsTooltip, Zoom]} />
                    <LayersDirective>
                        <LayerDirective shapeData={world_map} shapeSettings={{ fill: '#C1DFF5' }} markerClusterSettings={{ allowClustering: true, shape: 'Circle', height: 30, width: 30, labelStyle: { color: 'white' }, }}>
                            <MarkersDirective>
                                <MarkerDirective visible={true} dataSource={cluster} shape='Balloon' tooltipSettings={{ visible: true, valuePath: 'area', }} height={15} width={15} animationDuration={0}>
                                </MarkerDirective>
                            </MarkersDirective>
                        </LayerDirective>
                    </LayersDirective>
                </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

Refer the [`API`](../api/maps/markerSettingsModel/) for Marker feature.