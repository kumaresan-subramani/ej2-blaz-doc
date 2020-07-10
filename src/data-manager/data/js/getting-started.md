---
title: "HTML5 JavaScript DataManager | Getting started | Syncfusion"
component: "DataManager"
description: "Learn how to connect the JavaScript DataManager to a data source and perform queries against it. Also learn how to use DataManager with the JavaScript DataGrid Control"
---

# Getting started

This section explains you the steps required to create a simple Essential JS 2 Data Manager and demonstrate the basic usage of the Data Manager control in a JavaScript application.

## Dependencies

Below is the list of minimum dependencies required to use the DataManager.

```javascript
|-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-base
    |-- es6-promise (Required when window.Promise is not available)
```

> `@syncfusion/ej2-data` requires the presence of a Promise feature in global environment. In the browser, window.Promise must be available.

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 data manager control.

## Adding Syncfusion resources

The Essential JS 2 Data Manager control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global script from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the data manager and its dependencies scripts file into the `resources/scripts` folder.

Refer the below code to find location data manager's script file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-data/dist/global/ej2-data.min.js`

After copying the files, then you can refer the pager's scripts into the `index.html` file.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 Data Manager's dependent script -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Data Manager's global script -->
            <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script

Using CDN link, you can directly refer the data manager and its dependencies script into the `index.html`.

Refer the data manager's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js`](http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js)

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 Data Manager's dependent script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Pager's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

## Connection to a data source

The DataManager can act as gateway for both local and remote data source which will uses the query to interact with the data source.

### Binding to JSON data

`DataManager` can be bound to local data source by assigning the array of JavaScript objects to the `json` property or simply passing them
to the constructor while instantiating.

{% tab template="data/getting-started", es5Template="jsondata" %}

```typescript
import { DataManager, Query } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';
let compiledFunction: Function = compile(template);

let result: Object[] = new DataManager(data).executeLocal(new Query().take(8));

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

result.forEach((data: Object) => {
    table.appendChild(compiledFunction(data)[0]);
});

```

{% endtab %}

### Binding to OData

`DataManager` can be bound to remote data source by assigning service end point URL to the `url` property.
Now all `DataManager` operations will address the provided service end point.

{% tab template="data/getting-started", es5Template="bindodata" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>'

let compiledFunction: Function = compile(template);

const SERVICE_URI: string = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});

```

{% endtab %}

## Filter

The data filtering is a trivial operation which will let us to get reduced view of data based on filter criteria.
The filter expression can be built easily using `where` method of `Query` class.

{% tab template="data/getting-started", es5Template="filter" %}

```typescript
import { DataManager, Query } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';
let compiledFunction: Function = compile(template);

let result: Object[] = new DataManager(data).executeLocal(new Query().where('EmployeeID', 'equal', 3));

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

result.forEach((data: Object) => {
    table.appendChild(compiledFunction(data)[0]);
});

```

{% endtab %}

## Sort

The data can be ordered either in ascending or descending using `sortBy` method of `Query` class.

{% tab template="data/getting-started", es5Template="sort" %}

```typescript
import { DataManager, Query } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';
let compiledFunction: Function = compile(template);

let result: Object[] = new DataManager(data).executeLocal(new Query().sortBy('CustomerID').take(8));

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

result.forEach((data: Object) => {
    table.appendChild(compiledFunction(data)[0]);
});

```

{% endtab %}

## Page

The `page` method of the Query class is used to get range of data based on the page number and the total page size.

{% tab template="data/getting-started", es5Template="page" %}

```typescript
import { DataManager, Query } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';
let compiledFunction: Function = compile(template);

let result: Object[] = new DataManager(data).executeLocal(new Query().page(1, 8));

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

result.forEach((data: Object) => {
    table.appendChild(compiledFunction(data)[0]);
});

```

{% endtab %}

## Component binding

DataManager component can be used with Syncfusion components which supports data binding.

### Local data binding

A DataSource can be created in-line with other Syncfusion component configuration settings.

{% tab template="data/getting-started", es5Template="localdata" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { DataManager } from '@syncfusion/ej2-data';
import { data } from './datasource.ts';

(<HTMLTableElement>document.getElementById('datatable')).style.display = 'none';

let grid: Grid = new Grid({
    dataSource: new DataManager(data),
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 90, type: 'number' },
                { field: 'CustomerID', width: 120, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 90, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 120, format: 'yMd' },
    ],
    height: 315,
    allowPaging: false
});

grid.appendTo('#Grid');

```

{% endtab %}

### Remote data binding

To bind remote data to Syncfusion component, you can assign a service data as an instance of `DataManager` to the `dataSource` property.

{% tab template="data/getting-started", es5Template="remotedata" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { DataManager } from '@syncfusion/ej2-data';

(<HTMLTableElement>document.getElementById('datatable')).style.display = 'none';

const SERVICE_URI: string = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/?$top=20';

let grid: Grid = new Grid({
    dataSource: new DataManager({ url: SERVICE_URI }),
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 90, type: 'number' },
                { field: 'CustomerID', width: 120, headerText: 'Customer ID', type: 'string' },
                { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 90 }
    ],
    height: 315
});

grid.appendTo('#Grid');

```

{% endtab %}