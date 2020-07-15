---
title: "Drop-down list How to modify result data"
component: "DropDownList"
description: "This section explains on how to modify the result data before binding to the Syncfusion JavaScript drop-down list control."
---

# Modify the result data before passing to DropDownList when binding remote data source

When binding the remote data source, by using the [actionComplete](../../api/drop-down-list/#actioncomplete) event,
you can modify the result data before passing it to DropDownList.

The following sample demonstrate how to modify the result data.

{% tab template="dropdownlist/basic",es5Template="modify-result", sourceFiles ='app.ts,index.html,styles.css' %}

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
    actionComplete: function (e: any) {
        // initially result contains 6 items
        console.log("Before modified the result: " + e.result.length);
        // remove first 2 items from result.
        e.result.splice(0, 2);
        // now displays the result count is 4.
        console.log("After modified the result: " + e.result.length);
    }
});

//render the component
customers.appendTo('#ddlelement');

```

{% endtab %}