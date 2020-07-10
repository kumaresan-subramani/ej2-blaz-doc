---
title: "Data Binding"
component: "Pivot Table"
description: "Learn about how to bind local and remote data source to the pivot table."
---
# Data Binding

## JSON

For JSON data binding, the `type` property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html) needs to be set as `JSON`. By default, the default value is assumed as `JSON`.

### Binding JSON data via local

In-order to bind local JSON data to the pivot table user can assign the local variable holding the JSON data to the [`DataSource`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder~DataSource.html) property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html).

{% aspTab template="pivot-table/data-binding/local-data", sourceFiles="localdata.cs" %}

{% endaspTab %}

Using local variable, the JSON data can also be bound to the pivot table using [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) option with the help of `JsonAdaptor`. Here the instance of [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) holding JSON data is assigned to [`DataSource`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder~DataSource.html) property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html). The use of [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) is optional here.

{% aspTab template="pivot-table/data-binding/local-json-datamanager", sourceFiles="localjsondatamanager.cs" %}

{% endaspTab %}

![output](images/local-json-datamanager.png)

In the meantime, the JSON data from the local *.json file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to JSON data that can be assigned to the [`DataSource`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder~DataSource.html) property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html). The following code example illustrates the same.

```html
@using Syncfusion.EJ2.PivotView
@Html.EJS().Uploader("fileupload").Render()
@Html.EJS().PivotView("pivotview").Render()

<script>
    // Step 1: Initiate the file uploader
    var uploadObj = new.Uploader({});
    uploadObj.appendTo('#fileupload');
    var input = document.querySelector('input[type="file"]');
    // Step 2: Add the event listener which fires when the *.JSON file is uploaded.
    input.addEventListener('change', function (e) {
        // Step 3: Initiate the file reader
        var reader = new FileReader();
        reader.onload = function () {
            // Step 4: Getting the string output which is to be parsed as JSON.
            var result = JSON.parse(reader.result);
            var pivotObj = document.getElementById('pivotview');
            pivotObj.dataSourceSettings = {
                // Step 5: The JSON result to be bound as data source.
                dataSource: result
                // Step 6: The appropriate report needs to be provided here.
            }
        }
        reader.readAsText(input.files[0]);
    });
</script>
```

### Binding JSON data via remote

In-order to bind remote JSON data, mention the endpoint [`URL`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~Url.html) under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html) property. The [`URL`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~Url.html) property supports both direct downloadable file (*.json) and web service URL.

## CSV

For CSV data binding, the `type` property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html) needs to be set as `CSV` mandatorily.

### Binding CSV data via local

In-order to bind local CSV data to the pivot table, user needs to convert it as string array and then directly assign it to the [`DataSource`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder~DataSource.html) property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html).

{% aspTab template="pivot-table/data-binding/local-csv-data", sourceFiles="localcsvdata.cs" %}

{% endaspTab %}

![output](images/local-csv-data.png)

In the meantime, the CSV data from the local *.csv file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to string array that can be assigned to the [`DataSource`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder~DataSource.html) property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html). The following code example illustrates the same.

```html
@using Syncfusion.EJ2.PivotView
@Html.EJS().Uploader("fileupload").Render()
@Html.EJS().PivotView("pivotview").Render()

<script>
    // Step 1: Initiate the file uploader
    var uploadObj = new Uploader({});
    uploadObj.appendTo('#fileupload');
    var input = document.querySelector('input[type="file"]');
    // Step 2: Add the event listener which fires when the *.CSV file is uploaded.
    input.addEventListener('change', function (e) {
        // Step 3: Initiate the file reader
        var reader = new FileReader();
        reader.onload = function () {
            // Step 4: Getting the string output which is to be converted as string[][]
            var result = reader.result.split('\n').map(function (line) {
                return line.split(',');
            });
            var pivotObj = document.getElementById('pivotview');
            pivotObj.dataSourceSettings = {
                // Step 5: The string[][] result to be bound as data source
                dataSource: result,
                type: 'CSV'
                // Step 6: The appropriate report needs to be provided here.
            }
        };
        reader.readAsText(input.files[0]);
    });
</script>
```

### Binding CSV data via remote

In-order to bind remote CSV data, mention the endpoint [`URL`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~Url.html) under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html) property. The [`URL`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~Url.html) property supports both direct downloadable file (*.csv) and web service URL.

{% aspTab template="pivot-table/data-binding/remote-csv-data", sourceFiles="remotecsvdata.cs" %}

{% endaspTab %}

![output](images/remote-csv-data.png)

## Remote Data Binding

To interact with remote data source, provide the endpoint `Url` within `DataManager`. By default, `DataManager` uses `ODataAdaptor` for remote data-binding.

{% aspTab template="pivot-table/data-binding/remote-data", sourceFiles="remotedata.cs" %}

{% endaspTab %}

### Binding with OData services

OData is a standardized protocol for creating and consuming data. User can retrieve data from OData service using the `DataManager` class. Refer to the following code example for remote data binding using OData service.

{% aspTab template="pivot-table/data-binding/odata", sourceFiles="odata.cs" %}

{% endaspTab %}

### Binding with OData V4 services

The OData V4 is an improved version of OData protocols, and the `DataManager` class can be used to retrieve and consume OData V4 services. For more details on OData V4 services, refer to the [OData documentation](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). To bind OData V4 service, use the [`ODataV4Adaptor`](https://ej2.syncfusion.com/documentation/data/adaptors/#odatav4-adaptor).

{% aspTab template="pivot-table/data-binding/odatav4", sourceFiles="odatav4.cs" %}

{% endaspTab %}

### Web API

User can use `WebApiAdaptor` to bind pivot table with Web API created using OData endpoint.

{% aspTab template="pivot-table/data-binding/webapi", sourceFiles="web-api.cs" %}

{% endaspTab %}

## Values in row axis

By default, the value fields are plotted in column axis. To plot those fields in row axis, use the `valueAxis` property by setting its value as `row`. By default, it holds the value `column`.

{% aspTab template="pivot-table/data-binding/values-in-row", sourceFiles="valuesinrow.cs" %}

{% endaspTab %}

![output](images/valueaxis.png)

## Show 'no data' items

By default, the pivot table only shows the field item if it has data in its row or column combination. To show all items that do not have data in row and column combination in the pivot table, use the [`ShowNoDataItems`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewRow~ShowNoDataItems.html) property by settings its value to **true** for the desired fields. In the following code sample, rows of the "Country" and "Products" fields do not have data in all combination with "Year" and "Quarter" column field.

{% aspTab template="pivot-table/data-binding/no-data", sourceFiles="nodata.cs" %}

{% endaspTab %}

![output](images/nodata.png)

## Always shows the value headers

To show the value header always in pivot table even it holds a single value, use the [`AlwaysShowValueHeader`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~AlwaysShowValueHeader.html) property by settings its value as **true**.

{% aspTab template="pivot-table/data-binding/single-calculation-header", sourceFiles="single-calculation-header.cs" %}

{% endaspTab %}

![output](images/valuesheader.png)

## Customize empty value cells

User can show custom string in empty value cells using the [`EmptyCellsTextContent`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~EmptyCellsTextContent.html) property in [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html) class of the pivot table. Since the property is of string data type, user can fill empty value cells with any value like "0", "-", "*", "(blank)", etc. Its common for all value fields and can be configured through code behind.

{% aspTab template="pivot-table/data-binding/empty-cells", sourceFiles="empty-cells.cs" %}

{% endaspTab %}

![output](images/emptyvalues.png)

## Events

### Load

The event `Load` fires before initiate rendering of pivot table. In this event user can customize data source settings before initiating pivot table render module. It holds following parameters like `dataSourceSettings`, `fieldsType` and `pivotView`.

{% aspTab template="pivot-table/data-binding/load", sourceFiles="load.cs" %}

{% endaspTab %}

### EnginePopulated

The event `EnginePopulated` is triggered after engine is populated. It has following parameters - `dataSourceSettings`, `pivotFieldList` and `pivotValues`.

{% aspTab template="pivot-table/data-binding/engine-populated", sourceFiles="enginepopulated.cs" %}

{% endaspTab %}

### EnginePopulating

The event `EnginePopulating` triggers  before the pivot engine starts to populate and allows to customize the pivot datasource settings. It has following parameter `dataSourceSettings`.

{% aspTab template="pivot-table/data-binding/engine-populating", sourceFiles="enginepopulating.cs" %}

{% endaspTab %}

## See Also

* [Aggregation](./aggregation)
* [Show/Hide Totals](./summary-customization)
* [Customize number, date, and time values](./how-to/customize-number-date-and-time-values)