---
title: "HTML5 JavaScript DataManager | How To | Syncfusion"
component: "DataManager"
description: "Documentation on working in offline mode, sending additional parameters, and adding custom headers in the JavaScript DataManager"
---

# How To

## Work in offline mode

On remote data binding, every time invoking [`executeQuery`](../api/data/dataManager/#executequery) will send request to the server and the query will be processed on server-side. To avoid post back to server on calling [`executeQuery`](../api/data/dataManager/#executequery), you can set the **DataManager** to load all the data on initialization time and make the query processing in client-side.
To enable this behavior, you can use `offline` property of **DataManager**.

{% tab template="data/getting-started", es5Template="offline" %}

```typescript
import { DataManager, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/?$top=7';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

let dm: DataManager = new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor, offline: true });

dm.ready.then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
  });

```

{% endtab %}

> The loaded data will be cached in the `json` property of **DataManager**.

## Sending additional parameters to server

You can use the [`addParams`](../api/data/query/#addparams) method of [`Query`](../api/data/query) class, to add custom parameter to the data request.

{% tab template="data/getting-started", es5Template="withparameter" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().addParams('$top', '7'))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

## Adding custom headers

You can add custom headers to the request made by **DataManager** using the `headers` property.

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor, headers:[{ 'syncfusion': 'true' }] })
    .executeQuery(new Query())
    .then((e: ReturnOption) => {
        //get result from e.result
    });

```

> Adding custom headers while making cross domain request will initiate preflight request.