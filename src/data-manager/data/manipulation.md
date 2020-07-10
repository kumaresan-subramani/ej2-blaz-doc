---
title: "HTML5 JavaScript DataManager | CRUD Data operations | Syncfusion"
component: "DataManager"
description: "Learn how to create, update, and delete (CRUD) records from the data source by using various methods in the DataManager"
---

# CRUD Data operations

In this section, you will see in detail about how to manipulate data using **DataManager**. The **DataManager** can create, update and delete records either in local data source or remote data source.

Each data sources uses different way in handling the CRUD operations and hence **DataManager** uses data adaptors to manipulate data that can be understood by a particular data source.

## Insert

The [`insert`](../api/data/dataManager/#insert) method of **DataManager** is used to add new record to the data source. For remote data source, the new record will be send along with the request to the server.

{% tab template="data/manipulation", es5Template="insert" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

let table: HTMLTableElement = (<HTMLTableElement>document.getElementById('datatable'));
let dm: DataManager = new DataManager(data.slice(0, 4));

dm.executeQuery(new Query())
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
        });
    });

interface IOrder {
    OrderID: string;
    CustomerID: string;
    EmployeeID: string;
}

let button: HTMLInputElement = <HTMLInputElement>document.getElementById('manipulate');
let orderid: HTMLInputElement = <HTMLInputElement>document.getElementById('OrderID');
let cusid: HTMLInputElement = <HTMLInputElement>document.getElementById('CustomerID');
let empid: HTMLInputElement = <HTMLInputElement>document.getElementById('EmployeeID');


button.onclick = () => {
    let data: IOrder = {
        OrderID: orderid.value,
        CustomerID: cusid.value,
        EmployeeID: empid.value
    };
    if (!data.OrderID) { return; }
    dm.insert(data);
    dm.executeQuery(new Query())
        .then((e: ReturnOption) => {
            table.tBodies[0].innerHTML = '';
            (<Object[]>e.result).forEach((data: Object) => {
                table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
            });
        });
};
```

{% endtab %}

> In remote data sources, when the primary key field is an identity field, then it is advised to
return the created data in the response.

## Update

The [`update`](../api/data/dataManager/#update) method of **DataManager** is used to modify/update a record in the data source. For remote data source, the modified record will be send along with the request to the server.

{% tab template="data/manipulation", es5Template="update" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

let table: HTMLTableElement = (<HTMLTableElement>document.getElementById('datatable'));
let dm: DataManager = new DataManager(data.slice(0, 4));

dm.executeQuery(new Query())
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
        });
    });

let button: HTMLInputElement = <HTMLInputElement>document.getElementById('manipulate');
button.value = 'Update';
let orderid: HTMLInputElement = <HTMLInputElement>document.getElementById('OrderID');
let cusid: HTMLInputElement = <HTMLInputElement>document.getElementById('CustomerID');
let empid: HTMLInputElement = <HTMLInputElement>document.getElementById('EmployeeID');

interface IOrder {
    OrderID: number;
    CustomerID: string;
    EmployeeID: number;
}

button.onclick = () => {
    let data: IOrder = {
        OrderID: +orderid.value,
        CustomerID: cusid.value,
        EmployeeID: +empid.value
    };
    if (!data.OrderID) { return; }
    dm.update('OrderID', data);
    dm.executeQuery(new Query())
        .then((e: ReturnOption) => {
            table.tBodies[0].innerHTML = '';
            (<Object[]>e.result).forEach((data: Object) => {
                table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
            });
        });
};
```

{% endtab %}

> Primary key name is required by the [`update`](../api/data/dataManager/#update) method to find the record to be updated.

## Remove

The [`remove`](../api/data/dataManager/#remove) method of **DataManager** is used to remove a record from the data source. For remote data source, the record details such as primary key and data will be send along with the request to the server.

{% tab template="data/manipulation", es5Template="remove" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

let table: HTMLTableElement = (<HTMLTableElement>document.getElementById('datatable'));
let dm: DataManager = new DataManager(data.slice(0, 4));

dm.executeQuery(new Query())
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
        });
    });

let button: HTMLInputElement = <HTMLInputElement>document.getElementById('manipulate');
button.value = 'Remove';
let orderid: HTMLInputElement = <HTMLInputElement>document.getElementById('OrderID');
document.getElementById('CustomerID').style.display = 'none';
document.getElementById('EmployeeID').style.display = 'none';


button.onclick = () => {
    if (!orderid.value) { return; }
    dm.remove('OrderID', { OrderID: +orderid.value });
    dm.executeQuery(new Query())
        .then((e: ReturnOption) => {
            table.tBodies[0].innerHTML = '';
            (<Object[]>e.result).forEach((data: Object) => {
                table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
            });
        });
};
```

{% endtab %}

> Primary key name and its value are required to find the record to be removed.

## Batch Edit Operation

**DataManager** supports batch processing for the CRUD operations. You can use the [`saveChanges`](../api/data/dataManager/#savechanges) method to batch the edit operation. For remote data source, requests to add, remove and change are handled altogether at a time rather than passing the request separately for each operation.

{% tab template="data/batchedit", es5Template="batchedit" %}

```typescript
import { DataManager, Query, ReturnOption } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

let table: HTMLTableElement = (<HTMLTableElement>document.getElementById('datatable'));
let dm: DataManager = new DataManager({ json: (<Object[]>data).slice(0, 4) });

dm.executeQuery(new Query())
    .then((e: ReturnOption) => {
        (<Object[]>e.result).forEach((data: Object) => {
            table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
        });
    });
let changes: { changedRecords: Object[], addedRecords: Object[], deletedRecords: Object[] } = {
    changedRecords: [], addedRecords: [], deletedRecords: []
};
let orderid: HTMLInputElement = <HTMLInputElement>document.getElementById('OrderID');
let cusid: HTMLInputElement = <HTMLInputElement>document.getElementById('CustomerID');
let empid: HTMLInputElement = <HTMLInputElement>document.getElementById('EmployeeID');

document.getElementById('added').onclick = () => {
    changes.addedRecords.push({
        OrderID: +orderid.value,
        CustomerID: cusid.value,
        EmployeeID: +empid.value
    });
    orderid.value = cusid.value = empid.value = null;
};
document.getElementById('changed').onclick = () => {
    changes.changedRecords.push({
        OrderID: +orderid.value,
        CustomerID: cusid.value,
        EmployeeID: +empid.value
    });
    orderid.value = cusid.value = empid.value = null;
};
document.getElementById('deleted').onclick = () => {
    changes.deletedRecords.push({
        OrderID: +orderid.value,
        CustomerID: cusid.value,
        EmployeeID: +empid.value
    });
    orderid.value = cusid.value = empid.value = null;
};

document.getElementById('save').onclick = () => {
    dm.saveChanges(changes, 'OrderID');
    changes = { changedRecords: [], addedRecords: [], deletedRecords: [] };
    dm.executeQuery(new Query())
        .then((e: ReturnOption) => {
            table.tBodies[0].innerHTML = '';
            (<Object[]>e.result).forEach((data: Object) => {
                table.tBodies[0].appendChild(compiledFunction(data)[0].firstChild);
            });
        });
};
```

{% endtab %}