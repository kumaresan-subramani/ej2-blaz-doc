---
title: "Combo box Filtering"
component: "ComboBox"
description: "This section for Syncfusion JavaScript combo box control shows the built-in filtering support with a rich set of filtering configurations."
---

# Filtering

The ComboBox has built-in support to filter data items when `allowFiltering` is enabled. The filter
operation starts as soon as you start typing characters in the component.

To display filtered items in the popup, filter the required data and return it to the ComboBox
via [updateData](../api/combo-box/#updatedata) method by using the [filtering](../api/combo-box/#filtering) event.

The following sample illustrates how to query the data source and pass the data to the ComboBox
through the `updateData` method in `filtering` event.

{% tab template="combobox/basic", es5Template="basic-filter" %}

```typescript

import { ComboBox, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { DataManager, Query } from '@syncfusion/ej2-data';

let searchData: { [key: string]: Object; }[] = [
{ Index: "s1", Country: "California" }, { Index: "s2", Country: "Florida" },
{ Index: "s3", Country: "Alaska" }, { Index: "s4", Country: "Georgia" }
];
let filter: ComboBox = new ComboBox({
    //set the search data to dataSource property
    dataSource: searchData,
    //map the appropriate columns to fields property
    fields: { text: "Country", value: "Index" },
    //set the placeholder to ComboBox input
    placeholder:"Select a country",
    //enable to filtering in ComboBox
    allowFiltering: true,
    //sort the resulted items
    sortOrder: 'Ascending',
    //Bind the filter event
    filtering: function (e: FilteringEventArgs) {
        let query = new Query();
        //frame the query based on search string with filter type.
        query = (e.text != "") ? query.where("Country", "startswith", e.text, true) : query;
        //pass the filter data source, filter query to updateData method.
        e.updateData(searchData, query);
    }
});
filter.appendTo('#comboelement');

```

{% endtab %}

## Limit the minimum filter character

When filtering the list items, you can set the limit for character count to raise remote request and fetch
filtered data on the ComboBox. This can be done by manual validation within the filter event handler.

In the following example, the remote request does not fetch the search data until the search key contains three characters.

{% tab template="combobox/basic", es5Template="limit-filter" %}

```typescript

import { ComboBox, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

let searchData: DataManager = new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
});
let filter: ComboBox = new ComboBox({
    dataSource: searchData,
    query: new Query().select(['ContactName', 'CustomerID']).take(6),
    // map the appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // set placeholder to ComboBox input element
    placeholder:"Select a customer",
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //sort the resulted items
    sortOrder: 'Ascending',
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
filter.appendTo('#comboelement');

```

{% endtab %}

## Change the filter type

While filtering, you can change the filter type to `contains`,
`startsWith`, or `endsWith` for string type within the filter event handler.

In the following examples, data filtering is done with `endsWith` type.

{% tab template="combobox/basic", es5Template="change-filter" %}

```typescript

import { ComboBox, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
let searchData: DataManager = new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
});
let filter: ComboBox = new ComboBox({
    dataSource: searchData,
    query: new Query().select(['ContactName', 'CustomerID']).take(6),
    // map the appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // set placeholder to ComboBox input element
    placeholder:"Select a customer",
    //set the height of the popup element
    popupHeight: "250px",
    //sort the resulted items
    sortOrder: 'Ascending',
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //bind the filtering event handler
    filtering: (e: FilteringEventArgs) => {
        // load overall data when search key empty.
        if(e.text == '') e.updateData(searchData);
        else{
          let query: Query = new Query().select(['ContactName', 'CustomerID']);
          // change the type of filtering to endswith filtering
          query = (e.text !== '') ? query.where('ContactName', 'endswith', e.text, true) : query;
          e.updateData(searchData, query);
        }
    }
});
filter.appendTo('#comboelement');

```

{% endtab %}

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the DataManager. This can be done
by passing the fourth optional parameter of the `where` clause.

The following example shows how to perform case-sensitive filter.

{% tab template="combobox/basic", es5Template="case-sensitive-filter" %}

```typescript

import { ComboBox, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
// defined the dataManager
let searchData: DataManager = new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
});
let filter: ComboBox = new ComboBox({
    dataSource: searchData,
    query: new Query().select(['ContactName', 'CustomerID']).take(6),
    // map the appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // set placeholder to ComboBox input element
    placeholder:"Select a customer",
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the height of the popup element
    popupHeight: "250px",
    //bind the filtering event handler
    filtering: (e: FilteringEventArgs) => {
        // load overall data when search key empty.
        if(e.text == '') e.updateData(searchData);
        else{
          let query: Query = new Query().select(['ContactName', 'CustomerID']);
           //enable the case sensitive filtering by passing false to 4th parameter.
          query = (e.text !== '') ? query.where('ContactName', 'startswith', e.text, false) : query;
          e.updateData(searchData, query);
        }
    }
});
filter.appendTo('#comboelement');

```

{% endtab %}

## Diacritics Filtering

The ComboBox supports diacritics filtering which will ignore the [diacritics](https://en.wikipedia.org/wiki/Diacritic) and makes it easier to filter the results in international characters lists when the [ignoreAccent](../api/combo-box/#ignoreaccent) is enabled.

In the following sample,data with diacritics are bound as dataSource for ComboBox.

{% tab template="combobox/basic", es5Template="diacritics-filtering" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
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
    // initialize ComboBox component
    let comboObj: ComboBox = new ComboBox({
        //set the local data to dataSource property
        dataSource: data,
        // set the placeholder to ComboBox input element
        placeholder: 'e.g: aero',
        // enabled the ignoreAccent property for ignore the diacritics
        ignoreAccent: true,
        // set true for enable the filtering support.
        allowFiltering: true
    });
    comboObj.appendTo('#comboelement');

```

{% endtab %}

## See Also

* [How to acheive autofill while filtering](./how-to/autofill)
* [How to group the data using header](./grouping)