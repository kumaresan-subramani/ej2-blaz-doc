---
title: "Combo box Data binding"
component: "ComboBox"
description: "This section for Syncfusion JavaScript combo box control shows how to bind with local data source and how to fetch data from remote data service."
---

# Data Binding

The ComboBox loads the data either from local data sources or
remote data services using the [`dataSource`](../api/combo-box/#datasource) property. It supports
the data type of `array` or `DataManager`.

The ComboBox also supports different kinds of data services such as OData, OData V4, and Web API, and data formats such as XML, JSON, and JSONP with the help of `DataManager` adaptors.

| Fields | Type | Description |
|------|------|-------------|
| text |  `string` | Specifies the display text of each list item. |
| value |  `number or string` | Specifies the hidden data value mapped to each list item that should contain a unique value. |
| groupBy |  `string` | Specifies the category under which the list item has to be grouped. |
| iconCss |  `string` | Specifies the icon class of each list item. |

> When binding complex data to the ComboBox, fields should be mapped correctly. Otherwise, the selected item remains undefined.

## Binding local data

Local data can be represented in two ways as described below.

### 1. Array of simple data

The ComboBox has support to load array of primitive data such as strings and numbers. Here, both value and text field act the same.

{% tab template="combobox/getting-started", es5Template="basic", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf'];

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to ComboBox input element
    placeholder: "Select a game"
});

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');
```

{% endtab %}

### 2. Array of JSON data

The ComboBox can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [fields](../api/combo-box/#fields) property.

In the following example, `Id` column and `Game` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="combobox/basic", es5Template="data-local" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let sportsData: { [key: string]: Object }[] = [
    { Id: 'Game1', Game: 'Badminton' },
    { Id: 'Game2', Game: 'Basketball' },
    { Id: 'Game3', Game: 'Cricket' },
    { Id: 'Game4', Game: 'Football' },
    { Id: 'Game5', Game: 'Golf' }
];

//initiate the ComboBox
let comboBoxObject: ComboBox = new ComboBox({
    // bind the sports Data to datasource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { text: 'Game', value: 'Id' },
    //set the placeholder to ComboBox input
    placeholder:"Select a game"
});
//render the component
comboBoxObject.appendTo('#comboelement');

```

{% endtab %}

### 3. Array of Complex data

The ComboBox can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [fields](../api/combo-box/#fields) property.

In the following example, `Code.Id` column and `Country.Name` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="combobox/basic", es5Template="data-complex" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let countriesData: { [key: string]: Object }[] = [
        { Country: { Name: 'Australia' }, Code: { Id: 'AU' }},
        { Country: { Name: 'Bermuda' },Code: { Id: 'BM' }},
        { Country:{ Name: 'Canada'}, Code:{ Id: 'CA'} },
        { Country:{Name: 'Cameroon'}, Code:{ Id: 'CM'} },
        { Country:{Name: 'Denmark'}, Code:{ Id: 'DK' }},
        { Country:{Name: 'France'}, Code: { Id:'FR'} }
];

//initiate the ComboBox
let comboBoxObject: ComboBox = new ComboBox({
    // bind the sports Data to datasource property
    dataSource: countriesData,
    // maps the appropriate column to fields property
    fields: { text: 'Country.Name', value: 'Code.Id' },
    //set the placeholder to ComboBox input
    placeholder:"Select a country"
});
//render the component
comboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## Binding remote data

The ComboBox supports retrieval of data from remote data services with the help of `DataManager` component. The `Query` property is used to fetch
data from the database and bind it to the ComboBox.

In the following sample, displayed first 6 contacts from the `customer` table of `Northwind` Data Service.

{% tab template="combobox/basic", es5Template="data-remote" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let customers: ComboBox = new ComboBox({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
    //bind the Query instance to query property
    query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
    //map the appropriate columns to fields property
    fields: { text: 'ContactName', value: 'CustomerID' },
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the placeholder to ComboBox input
    placeholder:"Select a customer"
});

//render the component
customers.appendTo('#comboelement');

```

{% endtab %}

## See Also

* [How to acheive cascading](./how-to/cascading/)
* [How to load data using template](./templates/#item-template)
* [How to group the data using header](./grouping)
* [How to filter the bound data](./filtering)