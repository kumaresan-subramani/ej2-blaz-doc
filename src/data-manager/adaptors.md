---
title: "HTML5 JavaScript DataManager | Data Adaptors | Syncfusion"
component: "DataManager"
description: "Documentation on how to interact with a variety of services by using data adaptors, including UrlAdaptor, ODataAdaptor, ODataV4Adaptor, and WebApiAdaptor. Also details how to write custom adaptors"
---

# Data Adaptors

Each data source or remote service uses different way in accepting request and sending back the response. **DataManager** cannot anticipate every way a data source works. To tackle this problem the **DataManager** uses the adaptor concept to communicate with particular data source.

For local data sources, the role of the data adaptor is to query the JavaScript object array based on the **Query** object and manipulate them.

When comes with remote datasource, the data adaptor is used to send the request that the server can understand and process the server response.

The adaptor can be assigned using the `adaptor` property of the **DataManager**.

## Json adaptor

`JsonAdaptor` is used to query and manipulate JavaScript object array.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, JsonAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';
let compiledFunction: Function = compile(template);

let result: Object[] = new DataManager({ json: data, adaptor: new JsonAdaptor })
                                .executeLocal(new Query().take(8));

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

result.forEach((data: Object) => {
    table.appendChild(compiledFunction(data)[0]);
});

```

{% endtab %}

## Url adaptor

`UrlAdaptor` act as the base adaptor for interacting with remote data services. Most of the built-in adaptors are derived from the `UrlAdaptor`.

```typescript
import { DataManager, Query, UrlAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/actions';

new DataManager({
        url: SERVICE_URI,
        adaptor: new UrlAdaptor
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });

```

`UrlAdaptor` expects response as a JSON object with properties `result` and `count` which
contains the collection of entities and the total number of records respectively.

The sample response object should be as follows,

```json
{
    "result": [{..}, {..}, {..}, ...],
    "count": 67
}
```

## OData adaptor

[OData](http://www.odata.org/documentation/odata-version-3-0/) is standardized protocol for creating and consuming data. You can retrieve data from OData service using **DataManager**. The `ODataAdaptor` helps you to interact with OData service. You can refer to the following code example of remote Data binding using OData service.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});

```

{% endtab %}

> By default, `ODataAdaptor` is used by **DataManager**.

## ODataV4 adaptor

The ODataV4 is an improved version of OData protocols and the **DataManager** can also retrieve and consume OData v4 services. For more details on OData v4 Services, refer the [odata documentation](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). You can use the `ODataV4Adaptor` to interact with ODataV4 service.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, ReturnOption, ODataV4Adaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'http://services.odata.org/V4/Northwind/Northwind.svc/Orders/';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataV4Adaptor }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});

```

{% endtab %}

## Web API adaptor

You can use the `WepApiAdaptor` to interact with Web API created with OData endpoint. The `WebApiAdaptor` is extended from the `ODataAdaptor`. Hence to use `WebApiAdaptor`, the endpoint should understand the OData formatted queries send along with request.

To enable OData query option for Web API, please refer to the [documentation](https://docs.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/supporting-odata-query-options)

```typescript
import { DataManager, Query, WebApiAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/api';

new DataManager({
        url: SERVICE_URI,
        adaptor: new WebApiAdaptor
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

`WebApiAdaptor` expects JSON response from the server and the response object should contain properties `Items` and `Count` whose values are collection of entities and total count of the entities respectively.

The sample response object should look like below.

```json
{
    Items: [{..}, {..}, {..}, ...],
    Count: 830
}
```

## WebMethod Adaptor

The `WebMethodAdaptor` is used to bind data source from remote services and code behind methods. It can be enabled in Grid using Adaptor property of DataManager as `WebMethodAdaptor`.

For every operations, an AJAX post will be send to the specified data service.

```typescript
import { DataManager, Query, WebMethodAdaptor } from '@syncfusion/ej2-data';

let SERVICE_URI = 'Default.aspx/DataSource';

new DataManager({
        url: SERVICE_URI,
        adaptor: new WebMethodAdaptor
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

`WebMethodAdaptor` expects JSON response from the server and the response object should contain properties `result` and `count`
whose values are collection of entities and total count of the entities respectively.

The sample response object should look like below.

```json
{
    result: [{..}, {..}, {..}, ...],
    count: 830
}
```

> The controller method's data parameter name must be `value`.

## Writing custom adaptor

Sometimes the built-in adaptors does not meet your requirement. In such cases you can create your own adaptor.

To create and use custom adaptor, please refer to the below steps.

* Select an built-in adaptor which will act as base class for your custom adaptor.
* Override the desired method to achieve your requirement.
* Assign the custom adaptor to the `adaptor` property of **DataManager**.

For the sake of demonstrating custom adaptor approach, we are going to see how to add serial number for the records by overriding the built-in response processing using `processResponse` method of the `ODataAdaptor`.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

class SerialNoAdaptor extends ODataAdaptor {
    public processResponse(): Object {
        let i: number = 0;
        //calling base class processResponse function
        let original: Object[] = super.processResponse.apply(this, arguments);
        //Adding serial number
        original.forEach((item: Object) => item['Sno'] = ++i);
        return original;
    }
}

let template: string = '<tr><td>${Sno}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

table.innerHTML = '<tr><th>SNO</th><th>Customer ID</th><th>Employee ID</th></tr>';

new DataManager({ url: SERVICE_URI, adaptor: new SerialNoAdaptor }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});


```

{% endtab %}