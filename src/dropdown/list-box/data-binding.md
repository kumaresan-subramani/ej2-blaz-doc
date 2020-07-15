---
title: "ListBox data binding and initialization through HTML tags"
component: "ListBox"
description: "Typescript ListBox supports databinding with local data source, initialization through HTML select, ul and input tags."
---

# Data Binding

The ListBox loads the data either from local data sources or remote data services using the [`dataSource`](../api/list-box/#datasource) property. It supports
the data type of `array` or `DataManager`.

The ListBox also supports different kinds of data services such as OData, OData V4, and Web API, and data formats such as XML, JSON, and JSONP with the help of `DataManager` adaptors.

| Fields | Type | Description |
|------|------|-------------|
| [`text`](../api/list-box/fieldSettingsModel/#text) |  `string` | Specifies the display text of each list item. |
| [`value`](../api/list-box/fieldSettingsModel/#value) |  `string` | Specifies the hidden data value mapped to each list item that should contain a unique value. |
| [`groupBy`](../api/list-box/fieldSettingsModel/#groupby) |  `string` | Specifies the category under which the list item has to be grouped. |
| [`iconCss`](../api/list-box/fieldSettingsModel/#iconcss) |  `string` | Specifies the iconCss class that needs to be mapped. |
| [`htmlAttributes`](../api/list-box/fieldSettingsModel/#htmlattributes) |  `string` | Allows additional attributes to configure the elements in various ways to meet the criteria. |

> When binding complex data to the ListBox, fields should be mapped correctly. Otherwise, the selected item remains undefined.

## Local Data

Local data can be represented by the following ways as described below.

### Array of string

The ListBox has support to load array of primitive data such as strings or numbers. Here, both value and text field acts as same.

{% tab template="list-box/data-binding", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

// define array of string
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis', 'Basket Ball', 'Base Ball', 'Hockey', 'Volley Ball'];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: sportsData
});

listObj.appendTo('#listbox');

```

{% endtab %}

### Array of object

The ListBox can generate its list items through an array of object data. For this,
the appropriate columns should be mapped to the [`fields`](../api/list-box/#fields) property.

In the following example, `id` and `sports` column from complex data have been mapped to the `value` field and `text` field, respectively.

{% tab template="list-box/data-binding", es5Template="arrayobject", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

        import { ListBox } from '@syncfusion/ej2-dropdowns';

        let sportsData: { [key: string]: Object }[] = [
            { id: 'game1', sports: 'Badminton' },
            { id: 'game2', sports: 'Cricket'},
            { id: 'game3', sports: 'Football'},
            { id: 'game4', sports: 'Golf'},
            { id: 'game5', sports: 'Tennis'},
            { id: 'game6', sports: 'Basket Ball'},
            { id: 'game7', sports: 'Base Ball'},
            { id: 'game8', sports: 'Hockey'},
            { id: 'game9', sports: 'Volley Ball'}];

        // initialize ListBox component
        let listObj: ListBox = new ListBox({
            //set the dataSource property
            dataSource: sportsData,
            // maps the appropriate column to fields property
            fields: { text: 'sports', value: 'id' }
        });

        listObj.appendTo('#listbox');

```

{% endtab %}

### Array of complex object

The ListBox can generate its list items through an array of complex data. For this,
the appropriate columns should be mapped to the [`fields`](../api/list-box/#fields) property.

In the following example, `Sports.Name` column from complex data have been mapped to the `text` field.

{% tab template="list-box/data-binding", es5Template="arraycomplexobject", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

let sportsData: { [key: string]: Object }[] = [
    { Id: 'game1', Sports: { Name: 'Badminton'} },
    { Id: 'game2', Sports: { Name: 'Cricket'} },
    { Id: 'game3', Sports: { Name: 'Football'} },
    { Id: 'game4', Sports: { Name: 'Golf'} },
    { Id: 'game5', Sports: { Name: 'Tennis'} },
    { Id: 'game6', Sports: { Name: 'Basket Ball'} },
    { Id: 'game7', Sports: { Name: 'Base Ball'} },
    { Id: 'game8', Sports: { Name: 'Hockey'} },
    { Id: 'game9', Sports: { Name: 'Volley Ball'} }];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the dataSource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { text: 'Sports.Name' }
});

listObj.appendTo('#listbox');

```

{% endtab %}

> The ListBox has also be rendered through `<input>`, `<UL>`, `select` element.

## Remote Data

The ListBox supports retrieval of data from remote data services with the help of [`DataManager`](https://ej2.syncfusion.com/documentation/data/getting-started/) component. The [`Query`](../api/list-box/#query) property is used to fetch
data from the database and bind it to the ListBox.

The following sample displays the first 10 products from `Products` table of the `Northwind` Data Service.

{% tab template="list-box/remote-data", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';  

//initiates the component
let listObj: ListBox = new ListBox({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor
        }),
    //bind the Query instance to query property
    query: new Query().from('Products').select('ProductID,ProductName').take(10),
    //map the appropriate columns to fields property
    fields: { text: 'ProductName', value: 'ProductID' }

});


listObj.appendTo('#listbox');

```

{% endtab %}

## HTML element

The ListBox can be initialized different tags as described below.
Though it is initialized in different tags, the UI appearance and built-in features will behave in the same way.

### Select element

When a ListBox is initialized on `SELECT` element, the list items can be assigned
through the option tag of the HTML select element.

{% tab template="list-box/select-element", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

//initiates the component
let listObj: ListBox = new ListBox();


listObj.appendTo('#listbox');

```

{% endtab %}

### UL element

The ListBox can be initialized through `<UL>` element which contains a collection of `<LI>` element.
The `<LI>` items act as a popup list items of the ListBox. The inner text of the `<LI>` element
is considered both as text and value fields.

{% tab template="list-box/ul-element", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

//initiates the component
let listObj: ListBox = new ListBox();


listObj.appendTo('#listbox');

```

{% endtab %}

## See Also

* [How to render icons to the list box](./icons-and-templates/#icons)
* [How to render group based list box](./sorting-and-grouping/#grouping)
* [How to add items to the list box](./how-to/add-items)
* [How to scroll the items in the list box](./how-to/enable-scroller)