---
title: "Autocomplete Template"
component: "AutoComplete"
description: "This section for Syncfusion JavaScript autocomplete control shows how to customize the appearance of each item in the pop-up list using template option."
---

# Templates

The AutoComplete has been provided with several options to customize each list items, group title, header
and footer elements. It uses the Essential JS 2 [`Template engine`](../../common/template-engine) to compile
and render the elements properly.

## Item template

The content of each list item within the AutoComplete can be customized with the help of
[`itemTemplate`](../api/auto-complete#itemtemplate) property.

In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="autocomplete/item-template", es5Template="item-template", sourceFiles="app.ts,styles.css,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
    //map the appropriate columns to fields property
    fields: { value: 'FirstName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to itemTemplate property
    itemTemplate: "<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"
});

//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## Group template

The group header title under which appropriate sub-items are categorized can also be customize
with the help of [`groupTemplate`](../api/auto-complete#grouptemplate) property. This template is common
for both inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="autocomplete/item-template", es5Template="group-template", sourceFiles="app.ts" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, Predicate, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

// form  predicate to fetch the grouped data
let groupPredicate = new Predicate('City', 'equal', 'london').or('City', 'equal', 'seattle');

//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6)
        .where(groupPredicate),
    //map the appropriate columns to fields property
    fields: { value: 'FirstName', groupBy: 'City' },
    //set the placeholder to AutoComplete input
    placeholder: "Find an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to groupTemplate
    groupTemplate: "<strong>${City}</strong>"
});

//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## Header template

The header element is shown statically at the top of the suggestion list items
within the AutoComplete, and any custom element can be placed as a header element using
[`headerTemplate`](../api/auto-complete#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns similar to multiple columns of the grid.

{% tab template="autocomplete/header-template", es5Template="header-template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City', 'EmployeeID']).take(6),
    //map the appropriate columns to fields property
    fields: { value: 'FirstName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to header template
    headerTemplate: "<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",
    //set the value to item template
    itemTemplate: "<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>"
});

//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## Footer template

The AutoComplete has options to show a footer element at the bottom of the list items in the
suggestion list. Here, you can place any custom element as a footer element using
[`footerTemplate`](../api/auto-complete#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the AutoComplete.

{% tab template="autocomplete/footer-template", es5Template="footer-template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { AutoComplete, OpenEventArgs } from '@syncfusion/ej2-dropdowns';

let sportsData = ['Badminton', 'Basketball', 'Cricket', 'Football', 'Golf', 'Gymnastics', 'Hockey'];
//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    //bind the data manager instance to dataSource property
    dataSource: sportsData,
    //set the placeholder to AutoComplete input
    placeholder: "Find a game",
    open: (e: OpenEventArgs) => {
      let count = atcObject.getItems().length;
      //set the value to footerTemplate property
      let ele = document.getElementsByClassName('foot')[0];
      ele.innerHTML =  "Total list item: " + count;
    }
    //set the footer template
    footerTemplate: "<span class='foot'></span>"
});

//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## No records template

The AutoComplete is provided with support to custom design the suggestion list content when no data is
found and no matches found on search with the help of
[`noRecordsTemplate`](../api/auto-complete#norecordstemplate) property.

In the following sample, suggestion list content displays the notification of no data available.

{% tab template="autocomplete/norecords-template", es5Template="norecords-template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    //bind the data manager instance to dataSource property
    dataSource: [],
    //set the placeholder to AutoComplete input
    placeholder: "Find an item",
    //set the value to noRecords template
    noRecordsTemplate: "<span class='norecord'> NO DATA AVAILABLE</span>"
});

//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## Action failure template

There is also an option to custom design the suggestion list content when the data fetch request
fails at the remote server. This can be achieved using the
[`actionFailureTemplate`](../api/auto-complete#actionfailuretemplate) property.

In the following sample, when the data fetch request fails, the AutoComplete displays the notification.

{% tab template="autocomplete/norecords-template", es5Template="actionfailure-template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
        // use the wrong url to display the action failure template
        url: 'https://services.odata.org/V4/Northwind/Northwind.svcs/',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName']).take(6),
    //map the appropriate columns to fields property
    fields: { value: 'FirstName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find an employee ",
    //set the value to action failure template
    actionFailureTemplate: "<span class='action-failure'> Data fetch get fails</span>"

});

//render the component
atcObject.appendTo('#atcelement');

```

{% endtab %}

## See Also

* [How to acheive filtering](./filtering)
* [How to group the data using header](./grouping/#grouping)
* [How to show the list items with icon](./how-to/icon-support/)