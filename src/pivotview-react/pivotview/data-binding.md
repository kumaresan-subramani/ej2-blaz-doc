---
title: "Data Binding"
component: "Pivot Table"
description: "Learn about how to bind local and remote data source to the pivot table."
---

# Data Binding

## JSON

For JSON data binding, the `type` property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings) needs to be set as `JSON`. By default, the default value is assumed as `JSON`.

### Binding JSON data via local

In-order to bind local JSON data to the pivot table user can assign the local variable holding the JSON data to the [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings).

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

Using local variable, the JSON data can also be bound to the pivot table using [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) option with the help of `JsonAdaptor`. Here the instance of [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) holding JSON data is assigned to [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings). The use of [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) is optional here.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataManager, JsonAdaptorQuery, ReturnOption } from '@syncfusion/ej2-data';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{
  public pivotObj: PivotViewComponent;
  public dataSource: DataManager = new DataManager({
    json: pivotData,
    adaptor: new JsonAdaptor
  });
  public dataSourceSettings: IDataOptions = {
    dataSource: this.dataSource,
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
  };

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

In the meantime, the JSON data from the local *.json file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to JSON data that can be assigned to the [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings). The following code example illustrates the same.

```javascript

import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { Uploader } from '@syncfusion/ej2-inputs';

class App extends React.Component<{}, {}>{
  
  // Step 1: Initiate the file uploader
  public uploadObj: Uploader = new Uploader({
  });
  this.uploadObj.appendTo('#fileupload');

  let input = document.querySelector('input[type="file"]');
  // Step 2: Add the event listener which fires when the *.JSON file is uploaded.
  input.addEventListener('change', function (e: Event) {
    // Step 3: Initiate the file reader
    let reader: FileReader = new FileReader();
    reader.onload = function () {
      // Step 4: Getting the string output which is to be parsed as JSON.
      let result: string[][] = JSON.parse(reader.result as string);
      public dataSourceSettings: IDataOptions = {
        // Step 5: The JSON result to be bound as data source.
        dataSource: this.result
        // Step 6: The appropriate report needs to be provided here.
      }
      reader.readAsText((input as any).files[0]);
    }
  });
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={ d => this.pivotObj = d! } id = 'PivotView' height = { 350} dataSourceSettings = { this.dataSourceSettings } > </PivotViewComponent>
  }
}


ReactDOM.render(<App />, document.getElementById('pivotview'));

```

### Binding JSON data via remote

In-order to bind remote JSON data, mention the endpoint [`URL`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#url) under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings) property. The [`URL`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#url) property supports both direct downloadable file (*.json) and web service URL.

## CSV

For CSV data binding, the `type` property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings) needs to be set as `CSV` mandatorily.

### Binding CSV data via local

In-order to bind local CSV data to the pivot table, user needs to convert it as string array and then directly assign it to the [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings).

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx", compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { csvdata } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    dataSource: this.getCSVData(),
    type: 'CSV',
    expandAll: false,
    columns: [{ name: 'Item Type' }, { name: 'Sales Channel' } ],
    filters: [],
    drilledMembers: [{ name: 'Item Type', items: ['Baby Food'] }],
    formatSettings: [{ name: 'Total Cost', format: 'C0' }, { name: 'Total Revenue', format: 'C0' }, { name: 'Total Profit', format: 'C0' }],
    rows: [{ name: 'Region' }, { name: 'Country' }],
    values: [{ name: 'Total Cost' }, { name: 'Total Revenue' }, { name: 'Total Profit' }],
  }
  getCSVData(): string[][] {
    let dataSource: string[][] = [];
    let jsonObject: string[] = csvdata.split(/\r?\n|\r/);
    for (let i: number = 0; i < jsonObject.length; i++) {
        if (!isNullOrUndefined(jsonObject[i]) && jsonObject[i] !== '') {
            dataSource.push(jsonObject[i].split(','));
        }
    }
    return dataSource;
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

In the meantime, the CSV data from the local *.csv file type can also be connected to the pivot table via the file uploader option. Here, the resulting string after uploading the file needs to be converted to string array that can be assigned to the [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#datasource) property under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings). The following code example illustrates the same.

```javascript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { Uploader } from '@syncfusion/ej2-inputs';

class App extends React.Component<{}, {}>{
    // Step 1: Initiate the file uploader
    public uploadObj: Uploader = new Uploader({
    });
    this.uploadObj.appendTo('#fileupload');

    let input = document.querySelector('input[type="file"]');
    // Step 2: Add the event listener which fires when the *.CSV file is uploaded.
    input.addEventListener('change', function (e: Event) {
      // Step 3: Initiate the file reader
      let reader: FileReader = new FileReader();
      reader.onload = function () {
        // Step 4: Getting the string output which is to be converted as string[][].
        let result: string[][] = (reader.result as string).split('\n').map(function (line) {
            return line.split(',');
        });

        public dataSourceSettings: IDataOptions = {
        // Step 5: The string[][] result to be bound as data source
        dataSource: this.result,
        type: 'CSV',
        // Step 6: The appropriate report needs to be provided here.
        }
        reader.readAsText((input as any).files[0]);
      }
    });
    public pivotObj: PivotViewComponent;
    render() {
      return <PivotViewComponent  ref={ d => this.pivotObj = d! } id = 'PivotView' height = { 350} dataSourceSettings = { this.dataSourceSettings } > </PivotViewComponent>
    }
}


ReactDOM.render(<App />, document.getElementById('pivotview'));
```

### Binding CSV data via remote

In-order to bind remote CSV data, mention the endpoint [`URL`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#url) under [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings) property. The [`URL`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#url) property supports both direct downloadable file (*.csv) and web service URL.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataManager, ODataAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}>{
  
  this.pivotObj.dataSourceSettings = {
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
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Remote Data Binding

To interact with remote data source, provide the endpoint `url` within [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) along with appropriate `adaptor`. By default, [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) uses `ODataAdaptor` for remote data-binding.

### Binding with OData services

OData is a standardized protocol for creating and consuming data. User can retrieve data from OData service using the [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) class. Refer to the following code example for remote data binding using OData service.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataManager, ODataAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions;
  public pivotObj: PivotViewComponent;
  public dataSource: Promise<void> = new DataManager({
    url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/',
    adaptor: new ODataAdaptor,
    crossDomain: true
  }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {
    this.pivotObj.dataSourceSettings = {
      dataSource: e.result as IDataSet[],
      expandAll: true,
      filters: [],
      columns: [{ name: 'OrderDate'}, { name: 'ShipCity' }],
      rows: [{ name: 'OrderID' }, { name: 'CustomerID' }],
      values: [{ name: 'Freight' }]
    }
  });

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Binding with OData V4 services

The OData V4 is an improved version of OData protocols, and the [`DataManager`](https://ej2.syncfusion.com/react/documentation/data/) class can be used to retrieve and consume OData V4 services. For more details on OData V4 services, refer to the [OData documentation](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). To bind OData V4 service, use the [`ODataV4Adaptor`](https://ej2.syncfusion.com/react/documentation/data/adaptors/#odatav4-adaptor).

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataManager, ODataV4Adaptor, Query, ReturnOption } from '@syncfusion/ej2-data';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}>{
  public pivotObj: PivotViewComponent;
  public dataSource: DataManager = new DataManager({
    adaptor: new ODataV4Adaptor,
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Orders/?$top=7',
    crossDomain: true
  });
  public dataSourceSettings: IDataOptions = {
    dataSource: this.dataSource,
    expandAll: true,
    filters: [],
    columns: [{ name: 'OrderDate'}, { name: 'ShipCity' }],
    rows: [{ name: 'OrderID' }, { name: 'CustomerID' }],
    values: [{ name: 'Freight' }]
  };

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### Web API

User can use [`WebApiAdaptor`](https://ej2.syncfusion.com/react/documentation/data/adaptors/#web-api-adaptor) to bind pivot table with Web API created using OData endpoint.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataManager, WebApiAdaptor, Query, ReturnOption } from '@syncfusion/ej2-data';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

class App extends React.Component<{}, {}>{
  public dataSourceSettings: IDataOptions;
  public pivotObj: PivotViewComponent;
  public dataSource: Promise<void> = new DataManager({
    url: 'https://bi.syncfusion.com/northwindservice/api/orders',
    adaptor: new WebApiAdaptor,
    crossDomain: true
  }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {
    this.pivotObj.dataSourceSettings = {
      dataSource: e.result as IDataSet[],
      expandAll: true,
      filters: [],
      columns: [{ name: 'ProductName', caption: 'Product Name' }],
      rows: [{ name: 'ShipCountry', caption: 'Ship Country' }, { name: 'ShipCity', caption: 'Ship City' }],
      formatSettings: [{ name: 'UnitPrice', format: 'C0' }],
      values: [{ name: 'Quantity' }, { name: 'UnitPrice', caption: 'Unit Price' }]
    }
  });

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Values in row axis

By default, the value fields are plotted in column axis. To plot those fields in row axis, use the [`valueAxis`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettings/#valueaxis) property by setting its value as **row**. By default, it holds the value **column**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    valueAxis: 'row'
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Show 'no data' items

By default, the pivot table only shows the field item if it has data in its row or column combination. To show all items that do not have data in row and column combination in the pivot table, use the [`showNoDataItems`](https://ej2.syncfusion.com/react/documentation/api/pivotview/fieldOptionsModel/#shownodataitems) property by settings its value to **true** for the desired fields. In the following code sample, rows of the "County" and "State" fields do not have data in all combination with "Date" column field.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { noData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
     dataSource: noData,
        expandAll: true,
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        columns: [{ name: 'Date', showNoDataItems: true}],
        values: [{ name: 'Quantity', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country', showNoDataItems: true }, { name: 'State', showNoDataItems: true }],
        filters: []
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Show value headers always

To show value header always in pivot table, even if it holds a single value, use the [`alwaysShowValueHeader`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#alwaysshowvalueheader) property by settings its value as **true**.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C0' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }],
    alwaysShowValueHeader: true
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Customize empty value cells

User can show custom string in empty value cells using the [`emptyCellsTextContent`](https://ej2.syncfusion.com/react/documentation/api/pivotview/dataSourceSettingsModel/#emptycellstextcontent) property in [`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings). Since the property is of string data type, user can fill empty value cells with any value like "0", "-", "*", "(blank)", etc. Its common for all value fields and can be configured through code behind.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    emptyCellsTextContent: '*',
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2'}],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }
  public pivotObj: PivotViewComponent;
  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## Event

### Load

The event [`load`](https://ej2.syncfusion.com/react/documentation/api/pivotview#load) fires before initiate rendering of pivot table. It holds following parameters like[`dataSourceSettings`](https://ej2.syncfusion.com/react/documentation/api/pivotview#datasourcesettings), `fieldsType` and `PivotView`. In this event user can customize data source settings before initiating pivot table render module.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, LoadEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2'}],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }
  public pivotObj: PivotViewComponent;

  onLoad(args: LoadEventArgs): void {
      args.dataSourceSettings.emptyCellsTextContent = "###";
      args.dataSourceSettings.columns[0].caption = "Full Year";
      args.dataSourceSettings.expandAll = true;
  }

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} load={this.onLoad.bind(this)} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### EnginePopulated

The event [`enginePopulated`](https://ej2.syncfusion.com/react/documentation/api/pivotview#enginepopulated) is triggered after engine is populated. It has following parameters - `dataSourceSettings`, `pivotFieldList` and `pivotValues`.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, EnginePopulatedEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2'}],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }
  public pivotObj: PivotViewComponent;

  enginePopulated(args: EnginePopulatedEventArgs): void {
     // triggers after engine gets populated
  }

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} enginePopulated={this.enginePopulated.bind(this)} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

### EnginePopulating

The event [`enginePopulating`](https://ej2.syncfusion.com/react/documentation/api/pivotview#enginepopulating) triggers  before the pivot engine starts to populate and allows to customize the pivot datasource settings. It has following parameter `dataSourceSettings`.

{% tab template="pivot-table/default", sourceFiles="app/**/index.tsx",compileJsx=true %}

```typescript
import { IDataOptions, IDataSet, PivotViewComponent, EnginePopulatingEventArgs } from '@syncfusion/ej2-react-pivotview';
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { pivotData } from './datasource';

class App extends React.Component<{}, {}>{

  public dataSourceSettings: IDataOptions = {
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    dataSource: pivotData as IDataSet[],
    expandAll: false,
    filters: [],
    drilledMembers: [{ name: 'Country', items: ['France'] }],
    formatSettings: [{ name: 'Amount', format: 'C2'}],
    columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
    values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
    rows: [{ name: 'Country' }, { name: 'Products' }],
  }
  public pivotObj: PivotViewComponent;

  enginePopulating(args: EnginePopulatingEventArgs): void {
      args.dataSourceSettings.columns[0].caption = "Full Year";
      args.dataSourceSettings.expandAll = true;
  }

  render() {
    return <PivotViewComponent  ref={d => this.pivotObj = d!} id='PivotView' height={350} enginePopulating={this.enginePopulating.bind(this)} dataSourceSettings={this.dataSourceSettings}></PivotViewComponent>
  }
};

ReactDOM.render(<App />, document.getElementById('pivotview'));

```

{% endtab %}

## See Also

* [Aggregation](./aggregation)
* [Show/Hide Totals](./summary-customization)
* [Customize number, date, and time values](./how-to/customize-number-date-and-time-values)