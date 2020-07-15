---
title: "Drop-down list limit search"
component: "DropDownList"
description: "This section explains on how to limit the search result of the Syncfusion JavaScript drop-down list control."
---

# Limit the search result on filtering

The following example demonstrates about how to set limit the search result on filtering.

{% tab template="dropdownlist/basic", es5Template="limit-search", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { DropDownList, FilteringEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

let searchData: DataManager = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

let filter: DropDownList = new DropDownList({
    // set the remote data to dataSource property
    dataSource: searchData,
    // bind the Query instance to query property
    query: new Query().select(['ContactName', 'CustomerID']).take(7),
    // map the appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // set placeholder to DropDownList input element
    placeholder:"Select a name",
    // sort the resulted items
    sortOrder: 'Ascending',
    // set true to allowFiltering for enable filtering supports
    allowFiltering: true,
    // bind the filtering event handler
    filtering: (e: FilteringEventArgs) => {
        // set limit as 4 to search result
        let query: Query = new Query().select(['ContactName', 'CustomerID']).take(4);
        query = (e.text !== '') ? query.where('ContactName', 'startswith', e.text, true) : query;
        e.updateData(searchData, query);
    }
});
filter.appendTo('#ddlelement');

```

{% endtab %}