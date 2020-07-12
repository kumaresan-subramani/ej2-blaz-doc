# Populate Data

This section explains how to populate shape data for providing data input to maps control and usage of the DataSource property.

## Shape data

The shape data collection describes geographical shape information that can be obtained from
[GEOJSON format shapes](http://files2.syncfusion.com/dtsupport/uploads/user/uploads/Maps_GeoJSON.zip).

.\ Maps_GeoJSON\All Countries with States

## Data binding

The maps control supports data binding with the `dataSource` property in shape layers.

### Properties

The following properties in shape layers are used to bind data in maps control:

    * dataSource
    * shapeDataPath
    * shapePropertyPath

## Data source

The dataSource property accepts the collection values as input. For example, you can provide a list of objects as input.

## Shape data path

The `shapeDataPath` property is used to reference the data ID in DataSource. For example, population MapData contains data ids ‘Name’ and ‘Population’. The `shapeDataPath` and the `shapePropertyPath` properties are related to each other (refer to the `shapePropertyPath` for more details).

## Shape property path

The `shapePropertyPath` property is similar to the `shapeDataPath` that refers to the column name in the `data` property of shape layers to identify the shape. When the values of the `shapeDataPath` property in the `dataSource` property and the value of `shapePropertyPath` in the data property match, then the associated object from the `dataSource` is bound to the corresponding shape.

The datasource is populated with JSON data that relative to the shape data and stored in JSON object. The USA population as datasource is used for better understanding.

The populationdensity.js” file is used to store JSON data.

Refer to both shape data and datasource as illustrated in the following code example.

{% aspTab template="maps/populate-data", sourceFiles="populate-data.cs" %}

{% endaspTab %}

## Binding complex data source

You can bind the data field from data source to the maps in two different ways.

1. Bind the field name directly to the properties as [`ShapeDataPath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsLayer~ShapeDataPath.html), [`ColorValuePath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsBubble~ColorValuePath.html),
[`ValuePath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsBubble~ValuePath.html) and [`ShapeValuePath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsMarker~ShapeValuePath.html).

2. Bind the field name as `data.field` to the properties as [`ShapeDataPath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsLayer~ShapeDataPath.html), [`ColorValuePath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsBubble~ColorValuePath.html),
[`ValuePath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsBubble~ValuePath.html) and [`ShapeValuePath`](https://help.syncfusion.com/cr/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Maps.MapsMarker~ShapeValuePath.html).

The complex data source binding can be done as illustrated in the following code example.

{% aspTab template="maps/complex-data", sourceFiles="complex-data.cs" %}

{% endaspTab %}
