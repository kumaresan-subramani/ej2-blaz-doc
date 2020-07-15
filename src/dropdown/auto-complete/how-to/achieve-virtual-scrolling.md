---
title: "Autocomplete virtual scrolling"
component: "AutoComplete"
description: "This section explains how to acheive virtual scrolling functionality in autocomplete control."
---

# Virtual Scrolling

The Virtual Scrolling is used to display a large amount of data without buffering the entire load of a huge database record in the AutoComplete, that is, when scrolling, the request is sent and fetch some amount of data from the server dynamically. Using the `scroll` event, get the data and generate the list add to popup using the `addItem` method.

Refer to the following code sample for virtual scrolling.

{% tab template="autocomplete/virtual", es5Template="virtual", sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
import { Query, DataManager, ODataAdaptor } from '@syncfusion/ej2-data';



 let data: DataManager = new DataManager({
    url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/',
    crossDomain: true
});
    // initialize AutoComplete component
    let autoObj: AutoComplete = new AutoComplete({
        // bind the DataManager instance to dataSource property
        dataSource: data,
        // bind the Query instance to query property
        query: new Query().from('Customers').select('ContactName').take(7),
        // map the appropriate columns to fields property
        fields: { text: 'ContactName', value: 'ContactName' },
         // set the placeholder to AutoComplete input element
        placeholder: 'Select a customer',
        // sort the resulted items
        sortOrder: 'Ascending',
        // set the height of the popup element
        popupHeight: '200px',
        actionComplete: function (e: any) {
          let operator: Query =  new Query().from('Customers').select('ContactName');
          let start: number = 7;
          let end: number = 12;
          let listElement: HTMLElement = this.list;
          listElement.addEventListener('scroll', () => {
            if ((listElement.scrollTop + listElement.offsetHeight >= listElement.scrollHeight)) {
                let filterQuery = operator.clone();
                data.executeQuery(filterQuery.range(start, end)).then((event: any) => {
                    start = end;
                    end += 5;
                    autoObj.addItem(event.result as { [key: string]: Object }[]);
                }).catch((e: Object) => {
                });
            }
        });
    }
    });
    autoObj.appendTo('#atcelement');

```

{% endtab %}
