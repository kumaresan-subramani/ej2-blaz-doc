# Layers

The maps is maintained through `layers`, and it can accommodate one or more layers.

## Multilayer

The multilayer support allows you to load multiple shape files in a single container. This enables maps to display more information.

### Adding multiple layers to the maps

The shape layers are the core layers of a map. The multiple layers can be added in the shape layers as `subLayers` within the shape layers.

## Sub Layer

The subLayer is the collection of shape layers.

In this example, the world map shape is used as shape data by utilizing the `“WorldMap.json”` file in the following folder structure obtained from downloaded Maps_GeoJSON folder.

..\ Maps_GeoJSON\

Refer both shape data and shape settings as illustrated in the following code example.

{% aspTab template="maps/layers", sourceFiles="layers.cs" %}

{% endaspTab %}

## Displaying layer in the view

In Maps, you can load multiple shape files. Using the `BaseLayerIndex` property, you can select a layer to display on user interface.

In this example, we have loaded two layers with the World map and the United States map shape data and selected a layer using the `BaseLayerIndex` property to show that layer on the web page.

{% aspTab template="maps/layers/layerview", sourceFiles="layerview.cs" %}

{% endaspTab %}

Refer the [`API`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsLayer.html) for Layers feature.