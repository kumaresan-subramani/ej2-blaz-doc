---
title: "Data Binding"
component: "Pivot Table"
description: "Learn about how to bind local and remote data source to the pivot table."
---

# Data Binding

## JSON

For JSON data binding, the `type` property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) needs to be set as `JSON`. By default, the default value is assumed as `JSON`.

### Binding JSON data via local

In-order to bind local JSON data to the pivot table user can assign the local variable holding the JSON data to the [`dataSource`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/).

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

Using local variable, the JSON data can also be bound to the pivot table using [`DataManager`](https://ej2.syncfusion.com/javascript/documentation/api/data/dataManager/) option with the help of `JsonAdaptor`. Here the instance of [`DataManager`](https://ej2.syncfusion.com/javascript/documentation/api/data/dataManager/) holding JSON data is assigned to [`dataSource`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/). The use of [`DataManager`](https://ej2.syncfusion.com/javascript/documentation/api/data/dataManager/) is optional here.

{% tab template="pivot-table/pivot-table", es5Template="localjsondatamanager", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet } from '@syncfusion/ej2-pivotview';
import { DataManager, JsonAdaptor } from '@syncfusion/ej2-data';
import { pivotData } from './datasource.ts';

let result: DataManager = new DataManager({ json: pivotData, adaptor: new JsonAdaptor })
let pivotTableObj: PivotView = new PivotView({
    dataSourceSettings: {
        dataSource: result,
        expandAll: false,
        enableSorting: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    height: 350
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

In the meantime, the JSON data from the local *.json file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to JSON data that can be assigned to the [`dataSource`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/). The following code example illustrates the same.

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

In-order to bind remote JSON data, mention the endpoint [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) property. The [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) property supports both direct downloadable file (*.json) and web service URL.

## CSV

For CSV data binding, the `type` property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) needs to be set as `CSV` mandatorily.

### Binding CSV data via local

In-order to bind local CSV data to the pivot table, user needs to convert it as string array and then directly assign it to the [`dataSource`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/).

{% tab template="pivot-table/pivot-table", es5Template="localcsvdata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView } from '@syncfusion/ej2-pivotview';
import '../../../node_modules/es6-promise/dist/es6-promise';
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

In the meantime, the CSV data from the local *.csv file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to string array that can be assigned to the [`dataSource`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/). The following code example illustrates the same.

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

In-order to bind remote CSV data, mention the endpoint [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) under [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) property. The [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) property supports both direct downloadable file (*.csv) and web service URL.

{% tab template="pivot-table/pivot-table", es5Template="remotecsvdata", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView } from '@syncfusion/ej2-pivotview';
import '../../../node_modules/es6-promise/dist/es6-promise';

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

To interact with remote data source, provide the endpoint [`URL`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#url) within [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) along with appropriate [`adaptor`](https://ej2.syncfusion.com/documentation/data/adaptors.html?lang=typescript). By default, [`DataManager`](https://ej2.syncfusion.com/documentation/api/data/dataManager/) uses [`ODataAdaptor`](https://ej2.syncfusion.com/documentation/data/adaptors/#odata-adaptor) for remote data-binding.

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

## Values in row axis

By default, the value fields are plotted in column axis. To plot those fields in row axis, use the [`valueAxis`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#valueaxis) property by setting its value as **row**. By default, it holds the value **column**.

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

By default, the pivot table only shows the field item if it has data in its row or column combination. To show all items that do not have data in row and column combination in the pivot table, use the [`showNoDataItems`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/fieldOptions/#shownodataitems) property by settings its value to true for the desired fields. In the following code sample, rows of the "Country" and "State" fields do not have data in all combination with "Date" column field.

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

To show the value header always in pivot table, even if it holds a single value, use the [`alwaysShowValueHeader`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#alwaysshowvalueheader) property by settings its value as **true**.

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

User can show custom string in empty value cells using the [`emptyCellsTextContent`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/#emptycellstextcontent) property in [`dataSourceSettings`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/dataSourceSettings/) of the pivot table. Since the property is of string data type, user can fill empty value cells with any value like "0", "-", "*", "(blank)", etc. Its common for all value fields and can be configured through code behind.

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

The event [`load`]((https://ej2.syncfusion.com/javascript/documentation/api/pivotview#load)) fires before initiate rendering of pivot table. It holds following parameters like `dataSourceSettings`, `fieldsType` and `pivotView`. In this event user can customize data source settings before initiating pivot table render module.

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

The event [`enginePopulated`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#enginepopulated) is triggered after engine is populated. It has following parameters - `dataSourceSettings`, `pivotFieldList` and `pivotValues`.

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
    enginePopulated(args: EnginePopulatedEventArgs): void {
        args.dataSourceSettings.columns[0].caption = 'Total Population';
        args.dataSourceSettings.emptyCellsTextContent = '###'
    },
});
pivotTableObj.appendTo('#PivotTable');

```

{% endtab %}

### EnginePopulating

The event [`enginePopulating`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview#enginepopulating) triggers  before the pivot engine starts to populate and allows to customize the pivot datasource settings. It has following parameter `dataSourceSettings`.

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
    enginePopulating(args: EnginePopulatingEventArgs): void {
        args.dataSourceSettings.columns[0].caption = 'Total Population';
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