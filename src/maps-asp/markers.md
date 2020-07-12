# Markers

Markers are notes that are used to leave a message on the map. It indicates or marks a specific location with desired symbols on the maps.

The `dataSource` property has a list of objects that contains data for markers. By default, it displays the bound data at the specified latitude and longitude. Using the `visible` API, you can enable or disable the markers.

Marker can be set to map using the following two ways:

* Marker and marker template

* Adding marker objects to map.

## Marker and marker template

The `markerSettings.dataSource` property has a list of objects that contains the data for annotation. By default, it displays the bound data at the specified latitude and longitude. The `markerSettings.template` property is used for customizing the template for markers.

**Note:** The markerSettings property is an array property.

{% aspTab template="maps/markers/markers", sourceFiles="markers.cs" %}

{% endaspTab %}

## Adding marker objects to map

The "n" number of markers can be added to shape layers using the `markerSettings.dataSource` property. Each dataSource object contains the following list of properties:

label: Text that displays some information about the annotation in text format.
latitude: Latitude point that determines the y-axis position of annotation.
longitude: Longitude point that determine the x-axis position of annotation.

{% aspTab template="maps/markers/marker-label", sourceFiles="marker-label.cs" %}

{% endaspTab %}

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

{% aspTab template="maps/markers/shape", sourceFiles="shape.cs" %}

{% endaspTab %}

## Marker Zooming

The map is initially scaled to the center value based on the marker distance. This can be achieved by setting `shouldZoomInitially` property in `zoomSettings` as `true`.

{% aspTab template="maps/markers/marker-zoom", sourceFiles="marker-zoom.cs" %}

{% endaspTab %}

## Marker Cluster Expand

The cluster is formed by grouping an identical and non-identical marker from the surrounding area. By clicking on the cluster and setting `allowClusterExpand` property in `markerClusterSettings` as `true` to expand the identical markers. If you zoom in any of the locations of the cluster, the number on the cluster will decrease and the overlapping marker will be split into an individual marker on the map. When you zoom out, it will increase the marker count and then cluster it again.

{% aspTab template="maps/markers/cluster", sourceFiles="cluster.cs" %}

{% endaspTab %}

## Enable the Legend for map markers

The legend can be enabled for marker by setting the `legendSettings.type` to **Markers** and legend visible to true. Refer to the following code sample to enable the legend for the markers:

{% aspTab template="maps/markers/legend", sourceFiles="legend.cs" %}

{% endaspTab %}

## Marker Clustering

Maps provides support to hide and cluster markers when they overlap each other.

The number on a clusters indicates how many overlapped markers it contains. If you zoom any of the cluster locations, the number on the cluster will decrease and you will begin to see the individual markers on the map. When zooming out, the overlapping marker will increase so that you can cluster it again and increase the count over the cluster.

Using the `markerClusterSettings.allowClustering` API, you can enable or disable this cluster support. The `markerClusterSettings` API also helps to customize clusters.

The `MarkerClusterRendering` event occurs when each cluster is rendered. You can also use this to customize the cluster. The `markerClusterClick` and `markerClusterMouseMove` events on mouse move and on clicking the cluster.

{% aspTab template="maps/markers/marker-cluster", sourceFiles="marker-cluster.cs" %}

{% endaspTab %}

Refer to the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsMarker.html) for marker feature.