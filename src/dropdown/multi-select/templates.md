---
title: "Multiselect Template"
component: "MultiSelect"
description: "This section demonstrates the customization of the appearance of each item in the pop-up list of Syncfusion JavaScript multiselect control using template option."
---

# Templates

The MultiSelect has been provided with several options to customize each list item, group title,
selected value, header, and footer elements. It uses the Essential JS 2
[Template engine](../common/template-engine) to compile and render the elements properly.

## Item template

The content of each list item within the MultiSelect can be customized with the
help of [itemTemplate](../api/multi-select/#itemtemplate)
property.

In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="multiselect/item-template", es5Template="item-template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let msObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City','EmployeeID']).take(6),
    //map the appropriate columns to fields property
    fields: { text: 'FirstName', value: 'EmployeeID' },
    //set the placeholder to MultiSelect input
    placeholder:"Select an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to itemTemplate property
    itemTemplate:"<div><span class='name'>${FirstName}</span><span class ='city'>${City}</span></div>"
});

//render the component
msObject.appendTo('#select');

```

{% endtab %}

## Value template

The currently selected value that is displayed by default on the MultiSelect input element can be customized using the [valueTemplate](../api/multi-select/#valuetemplate) property.

In the following sample, the selected value is displayed as a combined text of both `FirstName` and `City`
in the MultiSelect input, which is separated by a hyphen.

{% tab template="multiselect/item-template", es5Template="value-template",sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let msObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City','EmployeeID']).take(6),
    //map the appropriate columns to fields property
    fields: { text: 'FirstName', value: 'EmployeeID' },
    //set the placeholder to MultiSelect input
    placeholder:"Select an employee",
    mode: 'Box',
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the template value to itemTemplate property
    itemTemplate:"<div><span class='name'>${FirstName}</span><span class ='city'>${City}</span></div>",
    //set the value to valueTemplate property
    valueTemplate:"<span>${FirstName} - ${City}</span>"
});

//render the component
msObject.appendTo('#select');

```

{% endtab %}

## Group template

The group header title under which appropriate sub-items are categorized can also be
customize with the help of
[groupTemplate](../api/multi-select/#grouptemplate) property.
This template is common for both inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="multiselect/item-template", es5Template="group-template",sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, Predicate , DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

// form  predicate to fetch the grouped data
let groupPredicate = new Predicate('City', 'equal','london').or('City','equal','seattle');

//initiates the component
let msObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City','EmployeeID']).take(5)
    .where(groupPredicate),
    //map the appropriate columns to fields property
    fields: { text: 'FirstName', value: 'EmployeeID', groupBy:'City' },
    //set the placeholder to MultiSelect input
    placeholder:"Select employees",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to groupTemplate
    groupTemplate:"<strong>${City}</strong>"
});

//render the component
msObject.appendTo('#select');

```

{% endtab %}

## Header template

The header element is shown statically at the top of the popup list items within the
MultiSelect, and any custom element can be placed as a header element using the
[headerTemplate](../api/multi-select/#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns
similar to multiple columns of the grid.

{% tab template="multiselect/header-template", es5Template="header-template",sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let msObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName', 'City','EmployeeID']).take(6),
    //map the appropriate columns to fields property
    fields: { text: 'FirstName', value: 'EmployeeID' },
    //set the placeholder to MultiSelect input
    placeholder:"Select employees",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to header template
    headerTemplate:"<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",
    //set the value to item template
    itemTemplate:"<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>"

});

//render the component
msObject.appendTo('#select');

```

{% endtab %}

## Footer template

The MultiSelect has options to show a footer element at the bottom of the list items in the popup list.
Here, you can place any custom element as a footer element using the [footerTemplate](../api/multi-select/#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the MultiSelect.

{% tab template="multiselect/footer-template", es5Template="footer-template",sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';

let sportsData = [ "Basketball", "Cricket", "Football", "Golf"];
//initiates the component
let msObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: sportsData ,
    //set the placeholder to MultiSelect input
    placeholder:"Select games",
    //set the value to footer template
    footerTemplate:"<span class='foot'> Total list items: "+ sportsData.length +"</span>"
});

//render the component
msObject.appendTo('#select');

```

{% endtab %}

## No records template

The MultiSelect is provided with support to custom design the popup list content when no data is found
and no matches found on search with the help of
[noRecordsTemplate](../api/multi-select/#norecordstemplate) property.

In the following sample, popup list content displays the notification of no data available.

{% tab template="multiselect/norecords-template", es5Template="no-records", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';

//initiates the component
let msObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: [],
    //set the placeholder to MultiSelect input
    placeholder:"Select an item",
    //set the value to noRecords template
    noRecordsTemplate:"<span class='norecord'> NO DATA AVAILABLE</span>"
});

//render the component
msObject.appendTo('#select');

```

{% endtab %}

## Action failure template

There is also an option to custom design the popup list content when the data fetch request
fails at the remote server. This can be achieved using the
[actionFailureTemplate](../api/multi-select/#actionfailuretemplate) property.

In the following sample, when the data fetch request fails, the MultiSelect displays the notification.

{% tab template="multiselect/norecords-template", es5Template="failure-template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let MultiSelectObject: MultiSelect = new MultiSelect({
    //bind the data manager instance to dataSource property
    dataSource: new DataManager({
            // Here, use the wrong url to display the action failure template
            url: 'https://services.odata.org/V4/Northwind/Northwind.svcs/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Employees').select(['FirstName']).take(6),
    //map the appropriate columns to fields property
    fields: { text: 'FirstName', value: 'EmployeeID' },
    //set the placeholder to MultiSelect input
    placeholder:"Select an employee",
    //set the value to action failure template
    actionFailureTemplate:"<span class='action-failure'> Data fetch get fails</span>"

});

//render the component
MultiSelectObject.appendTo('#select');

```

{% endtab %}

## See Also

* [How to bind the data](./data-binding)
* [How to group the data using header](./grouping)
* [How to customize the options in MultiSelect](./chip-customization)