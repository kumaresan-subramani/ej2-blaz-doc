---
title: "HTML5 JavaScript DataManager | Querying | Syncfusion"
component: "DataManager"
description: "Learn how to build queries to be executed by the JavaScript DataManager by using the Query class to select fields, sort, filter, and group rows of a data source"
---

# Querying

In this section, you will see in detail about how to build query using [`Query`](../api/data/query/) class and consume
the data source.

## Specifying resource name using `from`

The [`from`](../api/data/query/#from) method is used to specify the resource name or table name from where the data should be retrieved.

{% tab template="data/getting-started", es5Template="from" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().from('Orders').take(8)).then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

## Projection using `select`

The [`select`](../api/data/query/#select) method is used to select particular fields or columns from the data source.

{% tab template="data/getting-started", es5Template="select" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().select(['OrderID', 'CustomerID', 'EmployeeID']).take(8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

## Eager loading navigation properties

You can use the [`expand`](../api/data/query/#expand) method to eagerly load navigation properties. The navigation properties
values are accessed using appropriate field names separated by dot(.) sign.

{% tab template="data/getting-started", es5Template="navigation" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${Employee.FirstName}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

table.innerHTML = '<tr><th>OrderID</th><th>CustomerID</th><th>Employee Name</th></tr>';

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().expand('Employee').select(['OrderID', 'CustomerID', 'Employee.FirstName']).take(8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });
```

{% endtab %}

## Sorting

You can use the [`sortBy`](../api/data/query/#sortby) method to perform sort operation in the data source. Default sorting order is `ascending`. To change the sort order, either you can specify the second argument of [`sortBy`](../api/data/query/#sortby) as `descending` or use the [`sortByDesc`](../api/data/query/#sortbydesc) method.

{% tab template="data/getting-started", es5Template="sorting" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().sortBy('CustomerID', 'descending').take(8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });
```

{% endtab %}

> Multi sorting can be performed by simply chaining the multiple `sortBy` methods.

## Filtering

You can use the [`where`](../api/data/query/#where) method to build filter criteria which allows you to get reduced view of
records. The [`where`](../api/data/query/#where) method can also be chained to form multiple filter criteria.

{% tab template="data/getting-started", es5Template="filtering" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().where('EmployeeID', 'equal', 3).take(8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });


```

{% endtab %}

### Filter Operators

Filter operators are generally used to specify the filter type. The various filter operators supported by **DataManager** is listed below.

* greaterthan
* greaterthanorequal
* lessthan
* lessthanorequal
* equal
* notequal
* startswith
* endswith
* contains

> These filter operators are used for creating filter query using
[`where`](../api/data/query/#where) method and [`Predicate`](../api/data/predicate/) class.

### Build complex filter criteria using `Predicate`

Sometimes chaining [`where`](../api/data/query/#where) method is not sufficient to create very complex filter criteria, in such cases we can use [`Predicate`](../api/data/predicate/) class to create composite filter criteria.

{% tab template="data/getting-started", es5Template="predicate" %}

```typescript
import { DataManager, Query, ODataAdaptor, Predicate, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

//Building complex filter criteria using `Predicate`
let predicate: Predicate = new Predicate('EmployeeID', 'equal', 3);
predicate = predicate.or('EmployeeID', 'equal', 2);

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().where(predicate).take(8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

## Searching

You can use the [`search`](../api/data/query/#search) method to create search criteria, it differs from the filter in the way that search criteria will applied to all fields in the data source whereas filter criteria will be applied to a particular field.

{% tab template="data/getting-started", es5Template="search" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager(data)
    .executeQuery(new Query().search('VI', ['CustomerID']))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

> You can search particular fields by passing the field name collection in the second argument of [`search`](../api/data/query/#search) method.

## Grouping

**DataManager** allow you to group records by category.
The [`group`](../api/data/query/#group) method is used to add group query.

{% tab template="data/getting-started", es5Template="grouping" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${field} - ${key}</td><td></td><td></td></tr>${for(item of items)}<tr><td>${item.OrderID}</td><td>${item.CustomerID}</td><td>${item.EmployeeID}</td></tr>${/for}';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().group('CustomerID').take(8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

> Multiple grouping can be done by simply chaining the [`group`](../api/data/query/#group) method.

## Paging

You can query paged data using [`page`](../api/data/query/#page) method. This allow you to query particular set of records based on the page size and index.

{% tab template="data/getting-started", es5Template="paging" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().page(2, 8))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
    });

```

{% endtab %}

## Aggregation

The [`aggregate`](../api/data/query/#aggregate) method allows you to get aggregated value for a field based on the type. The built-in aggregate types are,

* sum
* average
* min
* max
* count
* truecount
* falsecount

{% tab template="data/getting-started", es5Template="aggregation" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);
let footerFn: Function = compile('<tr><td></td><td></td><td>Minimum: ${min}</td></tr>');

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().take(5).requiresCount().aggregate('min', 'EmployeeID'))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
        table.appendChild(footerFn({ min: e.aggregates['EmployeeID - min'] })[0]);
    });

```

{% endtab %}

## Hierarchical query

You can use the [`hierarchy`](../api/data/query/#hierarchy) method to build nested query. The hierarchical queries are commonly required when you use foreign key binding.

The [`foreignKey`](../api/data/query/#foreignkey) method is used to specify the key field of the foreign table and the second argument of the [`hierarchy`](../api/data/query/#hierarchy) method accepts a selector function which selects the records from the foreign table.

{% tab template="data/getting-started", es5Template="hierarchy" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>'
let group: string = '<tr><td colspan=3>' +
'<table id="datatable" class="e-table"><tr><th>ID</th><th>Price</th><th>Quantity</th></tr>' +
'${for(detail of Order_Details)}<tr><td>${detail.ProductID}</td><td>${detail.UnitPrice}</td><td>${detail.Quantity}</td></tr>${/for}' +
'<table></td></tr>';

let compiledFunction: Function = compile(template);
let groupFn = compile(group);

const SERVICE_URI =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor })
    .executeQuery(new Query().from('Orders').take(3).hierarchy(
                    new Query()
                        .foreignKey("OrderID")
                        .from("Order_Details")
                        .sortBy("Quantity"),
                    function () {
                        // Selective loading of child elements
                        return [10248, 10249, 10250]
                    }
                ))
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
            table.appendChild(groupFn(data)[0]);
        });
    });
```

{% endtab %}