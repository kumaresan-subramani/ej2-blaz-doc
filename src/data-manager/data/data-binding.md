---
title: "HTML5 JavaScript DataManager | Data Binding | Syncfusion"
component: "DataManager"
description: "Learn how to consume local and remote data sources using the JavaScript DataManager."
---

# Data Binding

**DataManager** supports both RESTful JSON data services binding and local JavaScript object array binding.

## Local data binding

**DataManager** can be bound to local data source by assigning the array of JavaScript objects to the `json` property or simply passing them
to the constructor while instantiating. Now the JavaScript object array can be queried and manipulated.

{% tab template="data/getting-started", es5Template="local" %}

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

## Remote data binding

**DataManager** can be bound to remote data source by assigning service end point URL to the `url` property. With the provided `url`, the **DataManager** handles all communication with the data server with help of queries.

When querying data, the **DataManager** will convert the query object(**Query**) into server request after calling [`executeQuery`](../api/data/dataManager/#executequery) and waits for the server response(`JSON` format).

{% tab template="data/getting-started", es5Template="remote" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

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

> The queried data will not be cached locally unless offline mode is enabled.

## See Also

* [Binding with OData service](./adaptors/#odata-adaptor)
* [Binding with ODataV4 service](./adaptors/#odatav4-adaptor)
* [Binding with Web API](./adaptors/#web-api-adaptor)
* [How to write custom adaptor](./adaptors/#writing-custom-adaptor)
* [How to work in offline mode](./how-to/#work-in-offline-mode)
* [How to send additional parameters](./how-to/#sending-additional-parameters-to-server)
* [How to add custom request headers](./how-to/#adding-custom-headers)
