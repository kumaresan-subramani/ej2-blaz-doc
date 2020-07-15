---
title: "Autocomplete Data binding"
component: "AutoComplete"
description: "This section for Syncfusion JavaScript autocomplete control shows how to bind with local data source and how to fetch data from remote data service."
---

# Data binding

The AutoComplete loads the data either from local data sources or remote data services using the [`dataSource`](../api/auto-complete/#datasource)
property. It supports the data type of array or
`DataManager`.

The AutoComplete also supports different kind of data services such as OData, OData V4, Web API and data formats such as XML, JSON, JSONP with the help of DataManager Adaptors.

| Fields | Type | Description |
|------|------|-------------|
| value |  `number or string` | Specifies the hidden data value mapped to each list item that should contain a unique value. |
| groupBy |  `string` | Specifies the category under which the list item has to be grouped. |
| iconCss |  `string` | Specifies the icon class of each list item. |

>While binding complex data to AutoComplete, fields should be mapped correctly. Otherwise, the selected
item remains undefined.

## Bind to local data

Local data can be represented in two ways as described below.

### Array of string

The AutoComplete has support to load array of primitive data such as strings and numbers.

{% tab template="autocomplete/getting-started", es5Template="basic", sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: string[] = ['Badminton', 'Basketball', 'Cricket', 'Football', 'Golf', 'Gymnastics', 'Hockey', 'Tennis'];

// initialize AutoComplete component
let atcObject: AutoComplete = new AutoComplete({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to AutoComplete input element
    placeholder: "Find a game"
});

// render initialized AutoComplete
atcObject.appendTo('#atcelement');
```

{% endtab %}

### Array of object

The AutoComplete can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [`fields`](../api/auto-complete/#fields) property.

In the following example, `Game` column from complex data have been mapped to the `value` field.

{% tab template="autocomplete/basic", es5Template="data-local", sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let sportsData: { [key: string]: Object }[] = [
    { Id: 'Game1', Game: 'Badminton' },
    { Id: 'Game2', Game: 'Basketball' },
    { Id: 'Game3', Game: 'Cricket' },
    { Id: 'Game4', Game: 'Football' },
    { Id: 'Game5', Game: 'Golf' },
    { Id: 'Game6', Game: 'Hockey' },
    { Id: 'Game7', Game: 'Rugby' },
    { Id: 'Game8', Game: 'Snooker' }
];

//initiate the AutoComplete
let atcObject: AutoComplete = new AutoComplete({
    // bind the sports Data to datasource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { value: 'Game' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a game"
});
//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

### Array of complex object

The AutoComplete can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [`fields`](../api/auto-complete/#fields) property.

In the following example, `Country.Name` column from complex data have been mapped to the `value` field.

{% tab template="autocomplete/basic", es5Template="data-complex", sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let countriesData: { [key: string]: Object }[] = [
        { Country: { Name: 'Australia' }, Code: { Id: 'AU' }},
        { Country: { Name: 'Bermuda' },Code: { Id: 'BM' }},
        { Country:{ Name: 'Canada'}, Code:{ Id: 'CA'} },
        { Country:{Name: 'Cameroon'}, Code:{ Id: 'CM'} },
        { Country:{Name: 'Denmark'}, Code:{ Id: 'DK' }},
        { Country:{Name: 'France'}, Code: { Id:'FR'} },
        { Country:{Name: 'Finland'}, Code:  { Id:'FI'} },
        { Country:{Name: 'Germany'}, Code: { Id:'DE'} },
        { Country:{Name: 'Greenland'}, Code:{ Id: 'GL' }},
        { Country:{Name: 'Hong Kong'}, Code: { Id:'HK'} },
        { Country:{Name: 'India'}, Code:{ Id: 'IN'} },
        { Country:{ Name: 'Italy'}, Code: { Id:'IT'} },
        { Country:{ Name: 'Japan'}, Code: { Id: 'JP'} },
        { Country:{Name: 'Mexico'}, Code: { Id: 'MX' }},
        { Country:{Name: 'Norway'}, Code: { Id: 'NO'} },
        { Country:{Name: 'Poland'}, Code: { Id: 'PL' }},
        { Country:{Name: 'Switzerland'}, Code: { Id: 'CH'} },
        { Country:{Name: 'United Kingdom'},Code: { Id: 'GB'} },
        { Country:{Name: 'United States'}, Code: { Id: 'US'} }
];

//initiate the AutoComplete
let atcObject: AutoComplete = new AutoComplete({
    // bind the sports Data to datasource property
    dataSource: countriesData,
    // maps the appropriate column to fields property
    fields: { value: 'Country.Name' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a country"
});
//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## Bind to remote data

The AutoComplete supports retrieval of data from remote data services with the help of
`DataManager` component. The [`Query`](../api/auto-complete/#query)
property is used to fetch data from the database and bind it to the AutoComplete.

The following sample displays the first 6 contacts from the `Customers` table of the `Northwind` data service.

{% tab template="autocomplete/basic", es5Template="data-remote", sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let customers: AutoComplete = new AutoComplete({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
    //map the appropriate columns to fields property
    fields: { value: 'ContactName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a customer",
    //sort the resulted items
    sortOrder: 'Ascending'
});

//render the component
customers.appendTo('#atcelement');

```

{% endtab %}

## See Also

* [How to load data using template](./templates/#item-template)
* [How to group the data using header](./grouping)
* [How to filter the bound data](./filtering)