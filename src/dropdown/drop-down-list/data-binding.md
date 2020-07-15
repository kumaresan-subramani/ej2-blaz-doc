---
title: "Drop-down list Data binding"
component: "DropDownList"
description: "This section for Syncfusion JavaScript drop-down list control shows how to bind with local data source and how to fetch data from remote data service."
---

# Data Binding

The DropDownList loads the data either from local data sources or
remote data services using the
[dataSource](../api/drop-down-list/#datasource) property. It supports
the data type of `array` or `DataManager`.

The DropDownList also supports different kinds of data services such as OData, OData V4, and Web API, and data formats such as XML, JSON, and JSONP with the help of `DataManager` adaptors.

| Fields | Type | Description |
|------|------|-------------|
| text |  `string` | Specifies the display text of each list item. |
| value |  `number or string` | Specifies the hidden data value mapped to each list item that should contain a unique value. |
| groupBy |  `string` | Specifies the category under which the list item has to be grouped. |
| iconCss |  `string` | Specifies the icon class of each list item. |

> When binding complex data to the DropDownList, fields should be mapped correctly. Otherwise, the selected item remains undefined.

## Binding local data

Local data can be represented in two ways as described below.

### 1. Array of simple data

The DropDownList has support to load array of primitive data such as strings and numbers. Here, both value and text field act the same.

{% tab template="dropdownlist/getting-started", es5Template="basic", sourceFiles="app.ts,index.html" %}

```typescript
import { DropDownList } from '@syncfusion/ej2-dropdowns';

// define the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize DropDownList component
let dropDownListObject: DropDownList = new DropDownList({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to DropDownList input element
    placeholder: "Select a game"
});

// render initialized DropDownList
dropDownListObject.appendTo('#ddlelement');
```

{% endtab %}

### 2. Array of JSON data

The DropDownList can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [fields](../api/drop-down-list/#fields) property.

In the following example, `Id` column and `Game` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="dropdownlist/basic",es5Template="data-local", sourceFiles="app.ts,index.html" %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let sportsData: { [key: string]: Object }[] = [
    { Id: 'game1', Game: 'Badminton' },
    { Id: 'game2', Game: 'Football' },
    { Id: 'game3', Game: 'Tennis' }
];

//initiate the DropDownList
let dropDownListObject: DropDownList = new DropDownList({
    // bind the sports Data to datasource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { text: 'Game', value: 'Id' },
    //set the placeholder to DropDownList input
    placeholder:"Select a game"
});
//render the component
dropDownListObject.appendTo('#ddlelement');

```

{% endtab %}

### 3. Array of Complex data

The DropDownList can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [fields](../api/drop-down-list/#fields) property.

In the following example, `Code.Id` column and `Country.Name` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="dropdownlist/basic",es5Template="data-complex", sourceFiles="app.ts,index.html" %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let countriesData: { [key: string]: Object }[] = [
        { Country: { Name: 'Australia' }, Code: { Id: 'AU' }},
        { Country: { Name: 'Bermuda' },Code: { Id: 'BM' }},
        { Country:{ Name: 'Canada'}, Code:{ Id: 'CA'} },
        { Country:{Name: 'Cameroon'}, Code:{ Id: 'CM'} },
        { Country:{Name: 'Denmark'}, Code:{ Id: 'DK' }},
        { Country:{Name: 'France'}, Code: { Id:'FR'} }
    ];

//initiate the DropDownList
let dropDownListObject: DropDownList = new DropDownList({
    // bind the sports Data to datasource property
    dataSource: countriesData,
    // maps the appropriate column to fields property
    fields: { text: 'Country.Name', value: 'Code.Id' },
    //set the placeholder to DropDownList input
    placeholder:"Select a country"
});
//render the component
dropDownListObject.appendTo('#ddlelement');

```

{% endtab %}

## Binding remote data

The DropDownList supports retrieval of data from remote data services with the help of `DataManager` component. The [Query](../api/drop-down-list/#query) property is used to fetch
data from the database and bind it to the DropDownList.

The following sample displays the first 6 contacts from “Customers” table of the `Northwind` Data Service.

{% tab template="dropdownlist/basic", es5Template="data-remote", sourceFiles="app.ts,index.html" %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let customers: DropDownList = new DropDownList({
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
    //set the placeholder to DropDownList input
    placeholder:"Select a customer",
    //sort the resulted items
    sortOrder: 'Ascending'
});

//render the component
customers.appendTo('#ddlelement');

```

{% endtab %}

## See Also

* [How to load data using template](./templates/#item-template)
* [How to group the data using header](./grouping)
* [How to filter the bound data](./filtering)
* [How to get the count of the data when using remote data](./how-to/remote-data-bind)
* [How to acheive cascading](./how-to/cascading/)
* [How to add item in between the options](./how-to/add-item/)
* [How to remove an item](./how-to/remove-item/)
* [How to preselect the items in dropdownlist](./how-to/multiple-cascading/)