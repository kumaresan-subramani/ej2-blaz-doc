# OpenStreetMap

The OpenStreetMap (OSM) is the world map built by a community of developers; it is free to use under an open license. It allows you to view geographical data in a collaborative way from anywhere on the earth. The OSM map provides small tile images to display the map area in the Maps component.

## Add OpenStreetMap

One of the most important features in EJ2 Maps component is the built-in online map provider support. By using this feature, you can render OpenStreetMap in the maps component. This provides the ability to visualize street map tiles without using any external shape files.

You can enable this feature by setting the value of `layerType` property to `OSM`

{% aspTab template="maps/map-providers/osm", sourceFiles="osm.cs" %}

{% endaspTab %}

## Zooming and panning

You can zoom and pan the OSM maps layer. Zooming helps you get a closer look at a particular area on a map for in-depth analysis. Panning helps you to move a map around to focus the targeted area.

{% aspTab template="maps/map-providers/osmzoom", sourceFiles="osmzoom.cs" %}

{% endaspTab %}

## Adding markers and navigation line

Markers can be added to the layers of OSM maps by setting the corresponding location's coordinates of latitude and longitude using `markerSettings` property. You can add navigation lines on top of an OSM maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the `navigationLineSettings` property.

{% aspTab template="maps/map-providers/osmmarker", sourceFiles="osmmarker.cs" %}

{% endaspTab %}

## Sublayer

You can render any GeoJSON shape as a sublayer on top of an OSM maps layer for highlighting a particular continent or country in OSM maps by adding another layer and specifying the type to SubLayer.