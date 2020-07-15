---
title: "ListBox drag and drop"
component: "ListBox"
description: "Typescript ListBox supports drag and drop with in single list box and between two list boxes."
---

# Drag and drop

The ListBox has support to drag an item or a group of selected items and drop it within the same list box or into another list box.

The elements can be customized on drag and drop by using the following events,

| Events | Description |
|------|------|-------------|
| [`dragStart`](../api/list-box/#dragstart) | Triggers when the selected element is being dragged. |
| [`drag`](../api/list-box/#drag) | Triggers when the selected element is being dragged. |
| [`drop`](../api/list-box/#drop) | Triggers when the selected element is being dropped. |

## Single listbox

To drag and drop an item or group of item within the list box can be achieved by setting [`allowDragAndDrop`](../api/list-box/#allowdraganddrop) property as `true`.

The following sample illustrates how to drag and drop an item within the same list box by enabling `allowDragAndDrop` property.

{% tab template="list-box/remote-data", es5Template="singlelist", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

let groupA: { [key: string]: Object }[] = [
    { "Name": "Australia", "Code": "AU" },
    { "Name": "Bermuda", "Code": "BM" },
    { "Name": "Canada", "Code": "CA" },
    { "Name": "Cameroon", "Code": "CM" },
    { "Name": "Denmark", "Code": "DK" },
    { "Name": "France", "Code": "FR" },
    { "Name": "Finland", "Code": "FI" },
    { "Name": "Germany", "Code": "DE" },
    { "Name": "Hong Kong", "Code": "HK" }
];

let listObj: ListBox = new ListBox({

    // Set the groupa data to the data source.
    dataSource: groupA,
    // Set allowDragAndDrop as `true`.
    allowDragAndDrop: true,

    // Map the appropriate columns to fields property.
    fields: { text: 'Name' }
});

listObj.appendTo('#listbox');

```

{% endtab %}

## Multiple listbox

To drag and drop an item or group of item between two list boxes can be achieved by setting `allowDragAndDrop` property as `true` and [`scope`](../api/list-box/#scope) property should be set to both the list boxes.

In the following sample, the `allowDragAndDrop` property is set as `true` and `scope` is set as `combined-list` to enable drop and drop in both list boxes.

{% tab template="list-box/multiple-list-box", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

let groupA: { [key: string]: Object }[] = [
    { "Name": "Australia", "Code": "AU" },
    { "Name": "Bermuda", "Code": "BM" },
    { "Name": "Canada", "Code": "CA" },
    { "Name": "Cameroon", "Code": "CM" },
    { "Name": "Denmark", "Code": "DK" },
    { "Name": "France", "Code": "FR" },
    { "Name": "Finland", "Code": "FI" },
    { "Name": "Germany", "Code": "DE" },
    { "Name": "Hong Kong", "Code": "HK" }
];

let groupB: { [key: string]: Object }[] = [
    { "Name": "India", "Code": "IN" },
    { "Name": "Italy", "Code": "IT" },
    { "Name": "Japan", "Code": "JP" },
    { "Name": "Mexico", "Code": "MX" },
    { "Name": "Norway", "Code": "NO" },
    { "Name": "Poland", "Code": "PL" },
    { "Name": "Switzerland", "Code": "CH" },
    { "Name": "United Kingdom", "Code": "GB" },
    { "Name": "United States", "Code": "US" }
];

let listObj: ListBox = new ListBox({

    scope: 'combined-list',

    // Set the groupa data to the data source.
    dataSource: groupA,

    // Set allowDragAndDrop as `true`.
    allowDragAndDrop: true,

    height: '290px',

    // Map the appropriate columns to fields property.
    fields: { text: 'Name' }
});

listObj.appendTo('#listbox1');

listObj = new ListBox({

    scope: 'combined-list',

    // Set the groupa data to the data source.
    dataSource: groupB,

    // Set allowDragAndDrop as `true`.
    allowDragAndDrop: true,

    height: '290px',

    // Map the appropriate columns to fields property.
    fields: { text: 'Name' }
});

listObj.appendTo('#listbox2');

```

{% endtab %}

## See Also

* [How to reorder the items in the list box](./dual-list-box#dual-list-box)