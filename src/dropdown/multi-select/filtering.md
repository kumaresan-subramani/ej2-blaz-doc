---
title: "Multiselect Filtering"
component: "MultiSelect"
description: "This section for Syncfusion JavaScript multiselect control shows the built-in filtering support with a rich set of filtering configurations."
---

# Filtering

The MultiSelect has built-in support to filter data items when [`allowFiltering`](../api/multi-select/#allowfiltering) is enabled. The filter
operation starts as soon as you start typing characters in the MultiSelect input.

To display filtered items in the popup, filter the required data and return it to the MultiSelect
via [updateData](../api/multi-select/filteringEventArgs/#updatedata) method by using the [filtering](../api/multi-select/#filtering) event.

The following sample illustrates how to query the data source and pass the data to the MultiSelect
through the `updateData` method in `filtering` event.

{% tab template="multiselect/basic", es5Template="basic-filtering" %}

```typescript

import { MultiSelect, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { DataManager, Query } from '@syncfusion/ej2-data';

let searchData: { [key: string]: Object; }[] = [
{ index: "s1", country: "Alaska" }, { index: "s2", country: "California" },
{ index: "s3", country: "Florida" }, { index: "s4", country: "Georgia" }
];
let filter: MultiSelect = new MultiSelect({
    dataSource: searchData,
    // map the appropriate column
    fields: { text: "country", value: "index" },
    // set placeholder to MultiSelect input element
    placeholder:"Select countries",
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //Bind the filter event
    filtering: function (e: FilteringEventArgs) {
        let query = new Query();
        //frame the query based on search string with filter type.
        query = (e.text != "") ? query.where("country", "startswith", e.text, true) : query;
        //pass the filter data source, filter query to updateData method.
        e.updateData(searchData, query);
    }
});
filter.appendTo('#select');

```

{% endtab %}

## Limit the minimum filter character

When filtering the list items, you can set the limit for character count to raise remote request and fetch
filtered data on the MultiSelect. This can be done by manual validation within the filter event handler.

In the following example, the remote request does not fetch the search data until the search key contains three characters.

{% tab template="multiselect/basic", es5Template="basic-char-limit"  %}

```typescript

import { MultiSelect, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
let searchData: DataManager = new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
});
let filter: MultiSelect = new MultiSelect({
    dataSource: searchData,
    query: new Query().select(['ContactName', 'CustomerID']).take(7),
    // map the appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // set placeholder to MultiSelect input element
    placeholder:"Select customers",
    //sort the resulted items
    sortOrder: 'Ascending',
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //bind the filtering event handler
    filtering: (e: FilteringEventArgs) => {
        // load overall data when search key empty.
        if(e.text == '') e.updateData(searchData);
        else{
           // restrict the remote request until search key contains 3 characters.
          if (e.text.length < 3) { return; }
          let query: Query = new Query().select(['ContactName', 'CustomerID']);
          query = (e.text !== '') ? query.where('ContactName', 'startswith', e.text, true) : query;
          e.updateData(searchData, query);
        }
    }
});
filter.appendTo('#select');

```

{% endtab %}

## Change the filter type

While filtering, you can change the filter type to `contains`,
`startsWith`, or `endsWith` for string type within the filter event handler.

In the following examples, data filtering is done with `endsWith` type.

{% tab template="multiselect/basic", es5Template="basic-filtering-type" %}

```typescript

import { MultiSelect, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
let searchData: DataManager = new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
});
let filter: MultiSelect = new MultiSelect({
    dataSource: searchData,
    query: new Query().select(['ContactName', 'CustomerID']).take(7),
    // map the appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // set placeholder to MultiSelect input element
    placeholder:"Select names",
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //set the height of the popup element
    popupHeight: "250px",
    //sort the resulted items
    sortOrder: 'Ascending',
    //bind the filtering event handler
    filtering: (e: FilteringEventArgs) => {
        // load overall data when search key empty.
        if(e.text == '') e.updateData(searchData);
        else{
          let query: Query = new Query().select(['ContactName', 'CustomerID']);
          // change the type of filtering
          query = (e.text !== '') ? query.where('ContactName', 'endswith', e.text, true) : query;
          e.updateData(searchData, query);
        }
    }
});
filter.appendTo('#select');

```

{% endtab %}

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the DataManager. This can be done
by passing the fourth optional parameter of the `where` clause.

The following example shows how to perform case-sensitive filter.

{% tab template="multiselect/basic", es5Template="basic-filtering-type-casing" %}

```typescript
import { MultiSelect, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';

let sportsData: { [key: string]: Object }[] = [
    { id: 'game1', sports: 'Badminton' },
    { id: 'game2', sports: 'Football' },
    { id: 'game3', sports: 'Tennis' },
    { id: 'game4', sports: 'Golf' },
    { id: 'game5', sports: 'Hockey' }
];
let filter: MultiSelect = new MultiSelect({
    dataSource: sportsData,
    // map the appropriate column
    fields: { text: 'sports', value: 'id' },
    // set placeholder to MultiSelect input element
    placeholder:"Select names",
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //set the height of the popup element
    popupHeight: "250px",
    //sort the resulted items
    sortOrder: 'Ascending',
    //bind the filtering event handler
    filtering: (e: FilteringEventArgs) => {
        // load overall data when search key empty.
        if(e.text == '') e.updateData(sportsData);
        else{
          let query: Query = new Query().select(['sports', 'id']);
           //enable the case sensitive filtering by passing false to 4th parameter.
          query = (e.text !== '') ? query.where('sports', 'startswith', e.text, false) : query;
          e.updateData(sportsData, query);
        }
    }
});
filter.appendTo('#select');
```

{% endtab %}

## Diacritics Filtering

The MultiSelect supports diacritics filtering which will ignore the [diacritics](https://en.wikipedia.org/wiki/Diacritic) and makes it easier to filter the results in international characters lists when the [ignoreAccent](../api/multi-select/#ignoreaccent) is enabled.

In the following sample,data with diacritics are bound as dataSource for MultiSelect.

{% tab template="multiselect/basic", es5Template="diacritics-filtering" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
    // create local data
    let data: string[] = [
        'Aeróbics',
        'Aeróbics en Agua',
        'Aerografía',
        'Aeromodelaje',
        'Águilas',
        'Ajedrez',
        'Ala Delta',
        'Álbumes de Música',
        'Alusivos',
        'Análisis de Escritura a Mano'];
    // initialize MultiSelect component
    let multiObj: MultiSelect = new MultiSelect({
        //set the local data to dataSource property
        dataSource: data,
        // set the placeholder to MultiSelect input element
        placeholder: 'e.g: aero',
        // enabled the ignoreAccent property for ignore the diacritics
        ignoreAccent: true,
        // set true for enable the filtering support.
        allowFiltering: true
    });
    multiObj.appendTo('#select');

```

{% endtab %}

## See Also

* [How to bind the data](./data-binding)
* [How to group the data using header](./grouping)
* [How to add custom value to the MultiSelect](./custom-value)