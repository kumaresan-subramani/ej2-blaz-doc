---
title: "Data Binding"
component: "Pivot Table"
description: "Learn about how to bind local and remote data source to the pivot table."
---
# Data Binding

## JSON

For JSON data binding, the `type` property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) needs to be set as `JSON`. By default, the default value is assumed as `JSON`.

### Binding JSON data via local

In-order to bind local JSON data to the pivot table user can assign the local variable holding the JSON data to the [`dataSource`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

{% tab template="pivot-table/pivot-table", es5Template="localdata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [],
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

Using local variable, the JSON data can also be bound to the pivot table using [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) option with the help of `JsonAdaptor`. Here the instance of [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) holding JSON data is assigned to [`dataSource`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/). The use of [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) is optional here.

{% tab template="pivot-table/pivot-table", es5Template="localjsondatamanager", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, JsonAdaptor } from '@syncfusion/ej2-data';
import { pivotData } from './datasource.ts';

let result: DataManager = new DataManager({ json: pivotData, adaptor: new JsonAdaptor })
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: result,
        drilledMembers: [{ name: 'Country', items: ['France'] }],
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

In the meantime, the JSON data from the local *.json file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to JSON data that can be assigned to the [`dataSource`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/). The following code example illustrates the same.

```javascript
import { PivotView } from '@syncfusion/ej2-pivotview';
import { Uploader } from '@syncfusion/ej2-inputs';

// Step 1: Initiate the file uploader
let uploadObj: Uploader = new Uploader({
});
uploadObj.appendTo('#fileupload');

let input = document.querySelector('input[type="file"]');
// Step 2: Add the event listener which fires when the *.JSON file is uploaded.
input.addEventListener('change', function (e: Event) {
    // Step 3: Initiate the file reader
    let reader: FileReader = new FileReader();
    reader.onload = function () {
        // Step 4: Getting the string output which is to be parsed as JSON.
        let result: any =JSON.parse(reader.result as string);
        let pivotGridObj: PivotView = new PivotView({
            dataSourceSettings: {
                // Step 5: The JSON result to be bound as data source.
                dataSource: result
                // Step 6: The appropriate report needs to be provided here.
            },
        });
        pivotGridObj.appendTo('#PivotTable');
    };
    reader.readAsText((input as any).files[0]);
});
```

### Binding JSON data via remote

In-order to bind remote JSON data, mention the endpoint [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) property. The [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) property supports both direct downloadable file (*.json) and web service URL.

{% tab template="pivot-table/pivot-table", es5Template="remotejsondata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView } from '@syncfusion/ej2-pivotview';

let pivotGridObj: PivotView = new PivotView({
    dataSourceSettings: {
        url: 'https://cdn.syncfusion.com/data/sales-analysis.json',
        expandAll: false,
        rows: [
            { name: 'Year', caption: 'Production Year' },
            { name: 'HalfYear', caption: 'Half Year' },
            { name: 'Quarter', caption: 'Quarter' }
        ],
        columns: [
            { name: 'EnerType', caption: 'Energy Type' },
            { name: 'EneSource', caption: 'Energy Source' }
        ],
        values: [
            { name: 'PowUnits', caption: 'Units (GWh)' },
            { name: 'ProCost', caption: 'Cost (MM)' }
        ],
        filters: []
    },
});
pivotGridObj.appendTo('#PivotTable');

```

{% endtab %}

## CSV

For CSV data binding, the `type` property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) needs to be set as `CSV` mandatorily.

> The CSV format is considered to be the most compact format compared to JSON since it is half the size of JSON. This helps to reduce the bandwidth while transferring to the browser.

### Binding CSV data via local

In-order to bind local CSV data to the pivot table, user needs to convert it as string array and then directly assign it to the [`dataSource`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/).

{% tab template="pivot-table/pivot-table", es5Template="localcsvdata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView } from '@syncfusion/ej2-pivotview';
import { csvdata } from './datasource.ts';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

let pivotObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: getCSVData(),
        type: 'CSV',
        expandAll: false,
        formatSettings: [{ name: 'Total Cost', format: 'C0' }, { name: 'Total Revenue', format: 'C0' }, { name: 'Total Profit', format: 'C0' }],
        drilledMembers: [{ name: 'Item Type', items: ['Baby Food'] }],
        rows: [
            { name: 'Region' },
            { name: 'Country' }
        ],
        columns: [
            { name: 'Item Type' },
            { name: 'Sales Channel' }
        ],
        values: [
            { name: 'Total Cost' },
            { name: 'Total Revenue' },
            { name: 'Total Profit' }
        ],
        filters: []
    },
    height: 290,
    width: '100%'
});
pivotObj.appendTo('#PivotTable');
function getCSVData(): string[][] {
    let dataSource: string[][] = [];
    let jsonObject: string[] = csvdata.split(/\r?\n|\r/);
    for (let i: number = 0; i < jsonObject.length; i++) {
        if (!isNullOrUndefined(jsonObject[i]) && jsonObject[i] !== '') {
            dataSource.push(jsonObject[i].split(','));
        }
    }
    return dataSource;
}

```

{% endtab %}

In the meantime, the CSV data from the local *.csv file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to string array that can be assigned to the [`dataSource`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/). The following code example illustrates the same.

```javascript
import { PivotView } from '@syncfusion/ej2-pivotview';
import { Uploader } from '@syncfusion/ej2-inputs';

// Step 1: Initiate the file uploader
let uploadObj: Uploader = new Uploader({
});
uploadObj.appendTo('#fileupload');
// Step 2: Add the event listener which fires when the *.CSV file is uploaded.
let input = document.querySelector('input[type="file"]');
input.addEventListener('change', function (e: Event) {
    // Step 3: Initiate the file reader
    let reader: FileReader = new FileReader();
    reader.onload = function () {
        // Step 4: Getting the string output which is to be converted as string[][].
        let result: string[][] = (reader.result as string).split('\n').map(function (line) {
            return line.split(',');
        });
        let pivotGridObj: PivotView = new PivotView({
            dataSourceSettings: {
                // Step 5: The string[][] result to be bound as data source.
                dataSource: result,
                type: 'CSV',
                // Step 6: The appropriate report needs to be provided here.
            },
        });
        pivotGridObj.appendTo('#PivotTable');
    };
    reader.readAsText((input as any).files[0]);
});
```

### Binding CSV data via remote

In-order to bind remote CSV data, mention the endpoint [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) property. The [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) property supports both direct downloadable file (*.csv) and web service URL.

{% tab template="pivot-table/pivot-table", es5Template="remotecsvdata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView } from '@syncfusion/ej2-pivotview';

let pivotObj: PivotView = new PivotView({
    dataSourceSettings: {
        url: 'https://bi.syncfusion.com/productservice/api/sales',
        type: 'CSV',
        expandAll: false,
        enableSorting: true,
        formatSettings: [{ name: 'Total Cost', format: 'C0' }, { name: 'Total Revenue', format: 'C0' }, { name: 'Total Profit', format: 'C0' }],
        drilledMembers: [{ name: 'Item Type', items: ['Baby Food'] }],
        rows: [
            { name: 'Region' },
            { name: 'Country' }
        ],
        columns: [
            { name: 'Item Type' },
            { name: 'Sales Channel' }
        ],
        values: [
            { name: 'Total Cost' },
            { name: 'Total Revenue' },
            { name: 'Total Profit' }
        ],
        filters: []
    },
    height: 300,
    width: '100%'
});
pivotObj.appendTo('#PivotTable');

```

{% endtab %}

## Remote Data Binding

To interact with remote data source, provide the endpoint `url` within [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) along with appropriate [`adaptor`](https://ej2.syncfusion.com/documentation/data/adaptors.html?lang=typescript). By default, [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) uses [`ODataAdaptor`](https://ej2.syncfusion.com/documentation/data/adaptors/#odata-adaptor) for remote data-binding.

{% tab template="pivot-table/pivot-table", es5Template="remotedata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: [],
        expandAll: true,
        filters: [],
        columns: [{ name: 'ProductName', caption: 'Product Name' }],
        rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
        formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
        values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

data.executeQuery(new Query().take(8)).then((e: ReturnOption) => {
    pivotTableObj.dataSourceSettings.dataSource = e.result as IDataSet[];
});

```

{% endtab %}

### Binding with OData services

OData is a standardized protocol for creating and consuming data. User can retrieve data from OData service using the [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/). Refer to the following code example for remote data binding using OData service.

{% tab template="pivot-table/pivot-table", es5Template="odata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, ODataAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new ODataAdaptor,
    crossDomain: true
});

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: data,
        expandAll: true,
        filters: [],
        columns: [{ name: 'CustomerID', caption: 'Customer Name' }],
        rows: [{ name: 'OrderID', caption: 'Order ID' },{name: 'OrderDate', caption:'Order Date' } ],
        values: [{ name: 'Freight' }]
    },
    height: 350,
    width: '100%',
    gridSettings: { columnWidth: 120 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Binding with OData V4 services

The OData V4 is an improved version of OData protocols, and the [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) can be used to retrieve and consume OData V4 services. For more details on OData V4 services, refer to the [OData documentation](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). To bind OData V4 service, use the [`ODataV4Adaptor`](https://ej2.syncfusion.com/documentation/data/adaptors/#odatav4-adaptor).

{% tab template="pivot-table/pivot-table", es5Template="odatav4", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, ODataAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: data,
        expandAll: true,
        filters: [],
        columns: [{ name: 'CustomerID', caption: 'Customer Name' }],
        rows: [{ name: 'OrderID', caption: 'Order ID' },{name: 'OrderDate', caption:'Order Date' } ],
        values: [{ name: 'Freight' }]
    },
    height: 350,
    width: '100%',
    gridSettings: { columnWidth: 120 }
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### Web API

User can use [`WebApiAdaptor`](https://ej2.syncfusion.com/documentation/data/adaptors/#web-api-adaptor) to bind pivot table with Web API created using OData endpoint.

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: data,
        expandAll: true,
        filters: [],
        columns: [{ name: 'ProductName', caption: 'Product Name' }],
        rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
        formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
        values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

## Mapping

One can define field information like alias name (caption), data type, aggregation type, show and hide subtotals etc. using the [`fieldMapping`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#fieldmapping) property under [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/). The available options are,

* [`name`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#name) - It is to specify the appropriate field name.
* [`caption`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#caption) - It is to set the alias name (caption) to the specific field. Instead of actual field name, the alias name (caption) will be set in the UI of the pivot table.
* [`type`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#type) - It is to display values in the pivot table with appropriate aggregation such as sum, product, count, average, minimum, maximum, etc. Its default value is **sum**. This option is applicable only for relational data source.
* [`axis`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#axis) - It will help to display the field in specified axis such as row/column/value/filter axis of the pivot table.
* [`showNoDataItems`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#shownodataitems) - It is to show all the members of a specific field to the pivot table, even if there are no data in the intersection of the row and column. The default value is **false**. This option is applicable only for relational data source.
* [`baseField`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#basefield) - For the aggregate types like "DifferenceFrom" or "PercentageOfDifferenceFrom" or "PercentageOfParentTotal", selective field is assigned for comparison via this property.
* [`baseItem`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#baseitem) For the aggregate types like "DifferenceFrom" or "PercentageOfDifferenceFrom" or "PercentageOfParentTotal", selective member in a field is assigned for comparison via this property.
* [`showSubTotals`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#showsubtotals) - It is to show or hide sub-totals of a specific field in row and column axis of the pivot table. The default value is **true**.
* [`isNamedSet`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#isnamedset) - It is to set whether the specified field is named set or not. In general, the named set is a set of dimension members or a set expression (MDX query) to be created as a dimension in the SSAS OLAP cube itself. The default value is **false** and this option is applicable only for OLAP data source.
* [`isCalculatedField`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#iscalculatedfield) - It is to set whether the specified field is a calculated field or not. In general, a calculated field is created from the bound data source or using simple formula with basic arithmetic operators in the pivot table. The default value is **false** and this option is applicable only for OLAP data source.
* [`showFilterIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#showfiltericon) - It is to show or hide the filter icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This filter icon is used to filter the members of a specified field at runtime in the pivot table. The default value is **true**.
* [`showSortIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#showsorticon) - It is to show or hide the sort icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This sort icon is used to order members of a specified field either in ascending or descending at runtime. The default value is **true**.
* [`showRemoveIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#showremoveicon) - It is to show or hide the remove icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This remove icon is used to remove the specified field during runtime. The default value is **true**.
* [`showValueTypeIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#showvaluetypeicon) - It is to show or hide the value type icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This value type icon helps to select the appropriate aggregation type to specified value field at runtime. The default value is **true**.
* [`showEditIcon`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#showediticon) - It is to show or hide the edit icon of a specific field which will be displayed on the button of the grouping bar and field list UI. This edit icon is used to modify caption, formula, and format of a specified calculated field at runtime. The default value is **true**.
* [`allowDragAndDrop`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#allowdraganddrop) - It is to restrict specific field's button from being dragged on runtime in the grouping bar and field list UI. This will prevent from altering the current report. The default value is **true**.
* [`dataType`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptionsModel/#datatype) - It is to specify the type of the field like 'string', 'number', 'datetime', 'date', and 'boolean'.

The main purpose of these mapping options is to configure each field that is not part of the initial pivot report. Even if any field that is part of this mapping is defined here, the value set in the initial report will have the highest preceding.

> This option is applicable only for relational data source.
In the below code sample, visibility of the field button icons are configured.

{% tab template="pivot-table/pivot-table", es5Template="field-mapping", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar, FieldList);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        allowLabelFilter: true,
        allowValueFilter: true,
        columns: [{ name: 'Year', caption: 'Production Year' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }],
        rows: [{ name: 'Country' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: [],
         fieldMapping: [
            { name: 'Quarter', showSortIcon: false },
            { name: 'Products', showFilterIcon: false, showRemoveIcon:false },
            { name: 'Amount', showValueTypeIcon: false, caption: 'Sold Amount' },
        ]
    },
    showGroupingBar: true,
    showFieldList: true,
    height: 340
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Values in row axis

By default, the value fields are plotted in column axis. To plot those fields in row axis, use the [`valueAxis`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#valueaxis) property by setting its value as **row**. By default, it holds the value **column**.

{% tab template="pivot-table/pivot-table", es5Template="valuesinrow", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [],
        valueAxis: 'row'
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Show 'no data' items

By default, the pivot table only shows the field item if it has data in its row or column combination. To show all items that do not have data in row and column combination in the pivot table, use the [`showNoDataItems`](https://ej2.syncfusion.com/documentation/api/pivotview/fieldOptions/#shownodataitems) property by settings its value to true for the desired fields. In the following code sample, rows of the "Country" and "State" fields do not have data in all combination with "Date" column field.

{% tab template="pivot-table/pivot-table", es5Template="nodata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { noData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: noData as IDataSet[],
        expandAll: true,
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        columns: [{ name: 'Date', showNoDataItems: true}],
        values: [{ name: 'Quantity', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country', showNoDataItems: true }, { name: 'State', showNoDataItems: true }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Always shows the value headers

To show the value header always in pivot table, even if it holds a single value, use the [`alwaysShowValueHeader`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#alwaysshowvalueheader) property by settings its value as **true**.

{% tab template="pivot-table/pivot-table", es5Template="single-calculation-header", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        filters: [],
        alwaysShowValueHeader: true
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Customize empty value cells

User can show custom string in empty value cells using the [`emptyCellsTextContent`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/#emptycellstextcontent) property in [`dataSourceSettings`](https://ej2.syncfusion.com/documentation/api/pivotview/dataSourceSettings/) of the pivot table. Since the property is of string data type, user can fill empty value cells with any value like "0", "-", "*", "(blank)", etc. Its common for all value fields and can be configured through code behind.

{% tab template="pivot-table/pivot-table", es5Template="empty-cells", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { noData } from './datasource.ts';

let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: noData as IDataSet[],
        expandAll: true,
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        columns: [{ name: 'Date', showNoDataItems: true}],
        values: [{ name: 'Quantity', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country', showNoDataItems: true }, { name: 'State', showNoDataItems: true }],
        filters: [],
        emptyCellsTextContent:'**'
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## Events

### Load

The event [`load`](https://ej2.syncfusion.com/documentation/api/pivotview#load) fires before initiate rendering of pivot table. In this event user can customize data source settings before initiating pivot table render module. It holds following parameters like `dataSourceSettings`, `fieldsType` and `pivotView`.

{% tab template="pivot-table/pivot-table", es5Template="onload", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar } from '@syncfusion/ej2-pivotview';
import { noData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
        dataSourceSettings: {
        dataSource: noData as IDataSet[],
        expandAll: true,
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        columns: [{ name: 'Date', showNoDataItems: true}],
        values: [{ name: 'Quantity', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country', showNoDataItems: true }, { name: 'State', showNoDataItems: true }],
        filters: [],
        emptyCellsTextContent:'**'
    },
    height: 350,
    load(args: LoadEventArgs): void {
        args.dataSourceSettings.columns[0].caption = 'Total Population';
        args.dataSourceSettings.emptyCellsTextContent = '###'
    },
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### EnginePopulated

The event [`enginePopulated`](https://ej2.syncfusion.com/documentation/api/pivotview#enginepopulated) is triggered after engine is populated. It has following parameters - `dataSourceSettings`, `pivotFieldList` and `pivotValues`.

{% tab template="pivot-table/pivot-table", es5Template="engine-populated", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar, EnginePopulatedEventArgs } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350,
    enginePopulated(args: EnginePopulatedEventArgs): void {
        //triggers after engine is populated
    },
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### EnginePopulating

The event [`enginePopulating`](https://ej2.syncfusion.com/documentation/api/pivotview#enginepopulating) triggers  before the pivot engine starts to populate and allows to customize the pivot datasource settings. It has following parameter `dataSourceSettings`.

{% tab template="pivot-table/pivot-table", es5Template="engine-populating", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, GroupingBar, EnginePopulatingEventArgs } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(GroupingBar);
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showGroupingBar: true,
    height: 350,
    enginePopulating(args: EnginePopulatingEventArgs): void {
        args.dataSourceSettings.columns[0].caption = 'Full Year';
        args.dataSourceSettings.emptyCellsTextContent = '###'
    },
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

## See Also

* [Aggregation](./aggregation)
* [Show/Hide Totals](./summary-customization)
* [Customize number, date, and time values](./how-to/customize-number-date-and-time-values)