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

{% aspTab template="pivot-table/data-binding/remote-json-data", sourceFiles="remotejsondata.cs" %}

{% endaspTab %}

## CSV

For CSV data binding, the `type` property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettingsBuilder_members.html) needs to be set as `CSV` mandatorily.

> The CSV format is considered to be the most compact format compared to JSON since it is half the size of JSON. This helps to reduce the bandwidth while transferring to the browser.

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

## Mapping

One can define field information like alias name (caption), data type, aggregation type, show and hide subtotals etc. using the [`FieldMapping`](https://help.syncfusion.com/cr/cref_files/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings~FieldMapping.html) property under [`PivotViewDataSourceSettings`](https://help.syncfusion.com/cr/aspnetmvc-js2/Syncfusion.EJ2~Syncfusion.EJ2.PivotView.PivotViewDataSourceSettings_members.html). The available options are,

* `name` - It is to specify the appropriate field name.
* `caption` - It is to set the alias name (caption) to the specific field. Instead of actual field name, the alias name (caption) will be set in the UI of the pivot table.
* `type` - It is to display values in the pivot table with appropriate aggregation such as sum, product, count, average, minimum, maximum, etc. Its default value is **sum**. This option is applicable only for relational data source.
* `axis` - It will help to display the field in specified axis such as row/column/value/filter axis of the pivot table.
* `showNoDataItems` - It is to show all the members of a specific field to the pivot table, even if there are no data in the intersection of the row and column. The default value is **false**. This option is applicable only for relational data source.
* `baseField` - For the aggregate types like "DifferenceFrom" or "PercentageOfDifferenceFrom" or "PercentageOfParentTotal", selective field is assigned for comparison via this property.
* `baseItem` For the aggregate types like "DifferenceFrom" or "PercentageOfDifferenceFrom" or "PercentageOfParentTotal", selective member in a field is assigned for comparison via this property.
*`showSubTotals` - It is to show or hide sub-totals of a specific field in row and column axis of the pivot table. The default value is **true**.
* `isNamedSet` - It is to set whether the specified field is named set or not. In general, the named set is a set of dimension members or a set expression (MDX query) to be created as a dimension in the SSAS OLAP cube itself. The default value is **false** and this option is applicable only for OLAP data source.
* `isCalculatedField` - It is to set whether the specified field is a calculated field or not. In general, a calculated field is created from the bound data source or using simple formula with basic arithmetic operators in the pivot table. The default value is **false** and this option is applicable only for OLAP data source.

* `showFilterIcon` - It is to show or hide the filter icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This filter icon is used to filter the members of a specified field at runtime in the pivot table. The default value is **true**.
* `showSortIcon` - It is to show or hide the sort icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This sort icon is used to order members of a specified field either in ascending or descending at runtime. The default value is **true**.
* `showRemoveIcon` - It is to show or hide the remove icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This remove icon is used to remove the specified field during runtime. The default value is **true**.
* `showValueTypeIcon` - It is to show or hide the value type icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This value type icon helps to select the appropriate aggregation type to specified value field at runtime. The default value is **true**.
* `showEditIcon` - It is to show or hide the edit icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This edit icon is used to modify caption, formula, and format of a specified calculated field at runtime. The default value is **true**.
* `allowDragAndDrop` - It is to restrict specific field's button from being dragged on runtime in the grouping bar and field list UI. This will prevent from altering the current report. The default value is **true**.
* `dataType` - It is to specify the type of the field like 'string', 'number', 'datetime', 'date', and 'boolean'.

The main purpose of these mapping options is to configure each field that is not part of the initial pivot report. Even if any field that is part of this mapping is defined here, the value set in the initial report will have the highest preceding.  
  
> This option is applicable only for relational data source.
In the below code sample, visibility of the field button icons are configured.

{% aspTab template="pivot-table/getting-start-mvc/field-mapping", sourceFiles="fieldmapping.cs" %}

{% endaspTab %}

![output](images/field-mapping.png)

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