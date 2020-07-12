# Markers

Markers are notes used to leave some message on the map.  It indicates or marks a specific location with desired symbols on the maps.

The `dataSource` property has a list of objects that contains data for markers. By default, it displays the bound data at the specified latitude and longitude. Using the `visible` API, you can enable or disable the markers.

There are two ways to set marker for map.

* Marker and marker template

* Adding marker objects to map.

## Marker and marker template

The `markerSettings.dataSource` property has a list of objects that contains the data for Annotation. By default, it displays the bound data at the specified latitude and longitude. The `markerSettings.template` property is used for customizing the template for markers.

**Note:** markerSettings is an Array property.

{% tab template="maps/default-map", es5Template="marker" %}

{% endtab %}

## Adding marker objects to map

The n number of markers can be added to shape layers with `markerSettings.dataSource` property. Each dataSource object contains the following list of properties.

* label - Text that displays some information about the annotation in text format.
* latitude - Latitude point determine the Y-axis position of annotation.
* longitude - Longitude point determine the X-axis position of annotation.

{% tab template="maps/default-map", es5Template="marker-object" %}

{% endtab %}

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

{% tab template="maps/default-map", es5Template="markerGroup" %}

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

{% tab template="maps/default-map", es5Template="markerColor" %}

{% endtab %}

## Marker Zooming

The map is initially scaled to the center value based on the marker distance. This can be achieved by setting `shouldZoomInitially` property in `zoomSettings` as `true`.

{% tab template="maps/default-map", es5Template="markerZooming" %}

{% endtab %}

## Marker Cluster Expand

The cluster is formed by grouping an identical and non-identical marker from the surrounding area. By clicking on the cluster and setting `allowClusterExpand` property in `markerClusterSettings` as `true` to expand the identical markers. If you zoom in any of the locations of the cluster, the number on the cluster will decrease and the overlapping marker will be split into an individual marker on the map. When you zoom out, it will increase the marker count and then cluster it again.

{% tab template="maps/default-map", es5Template="markerClusterExpand" %}

{% endtab %}

## Enable the Legend for map markers

Legend can be enabled for marker using `legendSettings.type` as **Markers** and legend visible as true.Refer the code snippet to enable the legend for the markers.

{% tab template="maps/default-map", es5Template="marker-legend" %}

{% endtab %}

## Marker Clustering

Maps provides support to hide and cluster markers when they overlap each other.

The number on a cluster indicates how many overlapped markers it contains. If you zoom any of the cluster locations, the number on the cluster will decrease and you will begin to see the individual markers on the map. When zooming out, the overlapping marker will increase so that you can cluster it again and increase the count over the cluster.

Using the [`markerClusterSettings.allowClustering`](../api/maps/markerClusterSettings/#allowclustering) API, you can enable or disable this cluster support. The [`markerClusterSettings`](../api/maps/markerClusterSettings) API also helps to customize clusters.

The [`MarkerClusterRendering`](../api/maps/iMarkerClusterRenderingEventArgs) event occurs when each cluster is rendered. You can also use this to customize the cluster. The [`markerClusterClick`](../api/maps/iMarkerClickEventArgs) and [`markerClusterMouseMove`](../api/maps/iMarkerClusterMoveEventArgs) events on mouse move and on clicking the cluster.

{% tab template= "maps/default-map", es5Template="cluster" %}

{% endtab %}

Refer the [`API`](../api/maps/markerSettingsModel/) for Marker feature.

## See Also

* [Add different types of markers](../maps/how-to/marker-type)
* [Tooltip for marker](../maps/how-to/marker-type)