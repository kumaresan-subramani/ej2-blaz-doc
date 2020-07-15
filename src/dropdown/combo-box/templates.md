---
title: "Combo box Template"
component: "ComboBox"
description: "This section for Syncfusion JavaScript combo box control shows the customization of the appearance of each item in the pop-up list using template option."
---

# Templates

The ComboBox has been provided with several options to customize each list item, group title,
selected value, header, and footer elements. It uses the Essential JS 2
[Template engine](../common/template-engine) to compile and render the elements properly.

## Item template

The content of each list item within the ComboBox can be customized with the
help of [itemTemplate](../api/combo-box/#itemtemplate)
property.

In the following sample, each list item is split into two columns to display relevant data's.

{% tab template="combobox/item-template", es5Template="item-template", sourceFiles="app.ts,styles.css,index.html" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let ComboBoxObject: ComboBox = new ComboBox({
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
    //set the placeholder to ComboBox input
    placeholder:"Select an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to itemTemplate property
    itemTemplate:"<span><span class='name'>${FirstName}</span><span class ='city'>${City}</span></span>"
});

//render the component
ComboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## Group template

The group header title under which appropriate sub-items are categorized can also be
customize with the help of
[groupTemplate](../api/combo-box/#grouptemplate) property.
This template is common for both inline and floating group header template.

In the following sample, employees are grouped according to their city.

{% tab template="combobox/item-template",es5Template="group-template", sourceFiles="app.ts" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, Predicate , DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

// form  predicate to fetch the grouped data
let groupPredicate = new Predicate('City', 'equal','london').or('City','equal','seattle');

//initiates the component
let ComboBoxObject: ComboBox = new ComboBox({
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
    //set the placeholder to ComboBox input
    placeholder:"Select an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to groupTemplate
    groupTemplate:"<strong>${City}</strong>"
});

//render the component
ComboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## Header template

The header element is shown statically at the top of the popup list items within the
ComboBox, and any custom element can be placed as a header element using the
[headerTemplate](../api/combo-box/#headertemplate) property.

In the following sample, the list items and its headers are designed and displayed as two columns
similar to multiple columns of the grid.

{% tab template="combobox/header-template", es5Template="header-template", sourceFiles="app.ts,styles.css" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let ComboBoxObject: ComboBox = new ComboBox({
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
    //set the placeholder to ComboBox input
    placeholder:"Select an employee",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to header template
    headerTemplate:"<span class='head'><span class='name'>Name</span><span class='city'>City</span></span>",
    //set the value to item template
    itemTemplate:"<span class='item' ><span class='name'>${FirstName}</span><span class='city'>${City}</span></span>"

});

//render the component
ComboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## Footer template

The ComboBox has options to show a footer element at the bottom of the list items in the popup list.
Here, you can place any custom element as a footer element using the [footerTemplate](../api/combo-box/#footertemplate) property.

In the following sample, footer element displays the total number of list items present in the ComboBox.

{% tab template="combobox/footer-template", es5Template="footer-template", sourceFiles="app.ts,styles.css" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';

let sportsData = ["Football", "BasketBall", "Golf", "Cricket"];
//initiates the component
let ComboBoxObject: ComboBox = new ComboBox({
    //bind the data manager instance to dataSource property
    dataSource: sportsData ,
    //set the placeholder to ComboBox input
    placeholder:"Select a game",
    //sort the resulted items
    sortOrder: 'Ascending',
    //set the value to footer template
    footerTemplate:"<span class='foot'> Total list items: "+ sportsData.length +"</span>"
});

//render the component
ComboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## No records template

The ComboBox is provided with support to custom design the popup list content when no data is found
and no matches found on search with the help of
[noRecordsTemplate](../api/combo-box/#norecordstemplate) property.

In the following sample, popup list content displays the notification of no data available.

{% tab template="combobox/norecords-template", es5Template="norecords-template", sourceFiles="app.ts,styles.css" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';

//initiates the component
let ComboBoxObject: ComboBox = new ComboBox({
    //bind the data manager instance to dataSource property
    dataSource: [],
    //set the placeholder to ComboBox input
    placeholder:"Select an item",
    //set the value to noRecords template
    noRecordsTemplate:"<span class='norecord'> NO DATA AVAILABLE</span>"
});

//render the component
ComboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## Action failure template

There is also an option to custom design the popup list content when the data fetch request
fails at the remote server. This can be achieved using the
[actionFailureTemplate](../api/combo-box/#actionfailuretemplate) property.

In the following sample, when the data fetch request fails, the ComboBox displays the notification.

{% tab template="combobox/norecords-template",es5Template="actionfailure-template", sourceFiles="app.ts" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
//import data manager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

//initiates the component
let ComboBoxObject: ComboBox = new ComboBox({
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
    //set the placeholder to ComboBox input
    placeholder:"Select an employee",
    //set the value to action failure template
    actionFailureTemplate:"<span class='action-failure'> Data fetch get fails</span>"

});

//render the component
ComboBoxObject.appendTo('#comboelement');

```

{% endtab %}

## See Also

* [How to acheive filtering](./filtering)
* [How to group the data using header](./grouping)
* [How to show the list items with icon](./how-to/icons-support/)