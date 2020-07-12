# Populate Data

This section explains how to populate data inputs and provide it to the Maps component.

## Shape Data

The Shape Data collection describing geographical shape information can be obtained from
[GEOJSON format shapes](http://files2.syncfusion.com/dtsupport/uploads/user/uploads/Maps_GeoJSON.zip).

.\ Maps_GeoJSON\All Countries with States

You can assign the complete contents in `“WorldMap”` file to new JSON object. For better understanding, a JSON file `“worldMap.json”` is already created to store JSON data in JSON object “world-map”.

## Data Binding

The Maps control supports data binding with the `dataSource` property in the shape layers.

### Properties

The following properties in shape layers is be used for binding data in Maps control,

    * dataSource
    * shapeDataPath
    * shapePropertyPath

## Data Source

The dataSource property accepts the collection values as input. For example, you can provide the list of objects as input.

## Shape Data Path

The `shapeDataPath` property is used to refer the data ID in DataSource. For example, population MapData contains data ids ‘Name’ and ‘Population’. The `shapeDataPath` and the `shapePropertyPath` properties are related to each other (refer to `shapePropertyPath` for more details).

## Shape Property Path

The `shapePropertyPath` property is similar to the `shapeDataPath` that refers to the column name in the `data` property of shape layers to identify the shape. When the values of the `shapeDataPath` property in the `dataSource` property and the value of `shapePropertyPath` in the data property match, then the associated object from the `dataSource` is bound to the corresponding shape.

The datasource is populated with JSON data relative to shape data and stored in JSON object. The USA population as datasource is used for better understanding.

Refer both shape data and datasource as illustrated in the following code example.

{% tab template= "maps/default-map", es5Template="population-data" %}

{% endtab %}

## Binding complex data source

You can bind the data field from data source to the maps in two different ways.

1. Bind the field name directly to the properties as [`shapeDataPath`](../api/maps/layerSettings/#shapedatapath), [`colorValuePath`](../api/maps/markerSettings/#colorvaluepath),
[`valuePath`](../api/maps/tooltipSettings/#valuepath) and [`shapeValuePath`](../api/maps/markerSettings/#shapevaluepath).

2. Bind the field name as `data.field` to the properties as [`shapeDataPath`](../api/maps/layerSettings/#shapedatapath), [`colorValuePath`](../api/maps/markerSettings/#colorvaluepath),
[`valuePath`](../api/maps/tooltipSettings/#valuepath) and [`shapeValuePath`](../api/maps/markerSettings/#shapevaluepath).

Refer complex support for data source as illustrated in the following code example.

{% tab template= "maps/default-map", es5Template="complexDataSource" %}

{% endtab %}