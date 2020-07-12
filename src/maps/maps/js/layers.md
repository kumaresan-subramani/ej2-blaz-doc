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

You can assign the complete contents in `USA.json` file to new JSON object. For better understanding, a JSON file `USA.json` is already created to store JSON data in JSON object usa_map and also copy the USA.json file data, bind value to “california” and “texas”.

{% tab template= "maps/default-map", es5Template="layers" %}

{% endtab %}

## Displaying layer in the view

In Maps, you can load multiple shape files. Using the `baseLayerIndex` property, you can select a layer to display on user interface.

In this example, we have loaded two layers with the World map and the United States map shape data and selected a layer using the `baseLayerIndex` property to show that layer on the web page.

{% tab template= "maps/default-map", es5Template="layerView" %}

{% endtab %}

If you set the `baseLayerIndex` value to 0, the world map will be loaded.

This concept is used in the Maps drill-down feature, so the corresponding shape will be loaded when clicking a shape of the maps.

Refer the [`API`](../api/maps/layerSettingsModel/) for Layers feature.

## See Also

* [Adding multiple layers in map](../maps/how-to/multiple-layer)
* [Display geometry shape in bing maps](../maps/how-to/bing-map)
* [Custom path map](../maps/how-to/custom-path)