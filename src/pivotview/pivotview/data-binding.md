---
title: "Data Binding"
component: "Pivot Table"
description: "Learn about how to bind local and remote data source to the pivot table."
---

# Data Binding

The pivot table uses `DataManager`, which supports both RESTful JSON data service binding and local JavaScript object array binding. The [`dataSource`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.PivotViewDataSourceSettings%601~DataSource.html) property can be assigned either with the instance of `DataManager` or list of objects. It supports two kinds of data binding method:

* Local data
* Remote data

## Local Data

To bind local data to the pivot table, user can assign a JavaScript object array to the [`dataSource`](https://help.syncfusion.com/cr/cref_files/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.PivotViewDataSourceSettings%601~DataSource.html) property under [`dataSourceSettings`](https://help.syncfusion.com/cr/blazor/Syncfusion.EJ2.Blazor~Syncfusion.EJ2.Blazor.PivotView.DataSourceSettingsModel%601.html). The local data source can also be provided as an instance of the `DataManager`.

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

> By default, `DataManager` uses `JsonAdaptor` for local data-binding.

## Remote Data

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

By default, the pivot table only shows the field item if it has data in its row or column combination. To show all items that do not have data in row and column combination in the pivot table, use the [`showNoDataItems`](https://ej2.syncfusion.com/javascript/documentation/api/pivotview/fieldOptions/#shownodataitems) property by settings its value to true for the desired fields. In the following code sample, rows of the "County" and "State" fields do not have data in all combination with "Date" column field.

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

## Event

The event `load` fires before initiate rendering of pivot table. It holds following parameters like dataSourceSettings, fieldsType and pivotView. In this event user can customize data source settings before initiating pivot table render module.

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

## See Also

* [Aggregation](./aggregation)
* [Show/Hide Totals](./summary-customization)
* [Customize number, date, and time values](./how-to/customize-number-date-and-time-values)