# Map Providers

The maps control supports map providers such as OpenStreetMap that can be added to any layers in maps.

## Open street map

`OpenStreetMap` is a map of the entire world. The OpenStreetMap allows you to view, edit and use geographical data in a collaborative way from any place on the earth.

### Enable OSM

You can enable this feature by setting the value of the layerType property value to “OSM” as illustrated in the following code example.

{% aspTab template="maps/map-providers/osm", sourceFiles="osm.cs" %}

{% endaspTab %}

#### URL Template

The `urlTemplate` property determines the format of tile map. You can specify the template for the tile layer.

## Bing map

Bing map is a key feature in accessing the external geospatial imagery services for deep-zoom satellite view.

### Enable Bing maps

You can enable this feature by defining the layerType to “bing”. The type of Bing map can be rendered as aerial, aerialwithlabel and road.

{% aspTab template="maps/map-providers/bing", sourceFiles="bing.cs" %}

{% endaspTab %}

#### Key

The Bing map key is provided as input to this key property. The Bing map key can be obtained from [http://www.microsoft.com/maps/create-a-bing-maps-key.aspx](http://www.microsoft.com/maps/create-a-bing-maps-key.aspx).
