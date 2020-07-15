---
title: "ListBox toolbar support"
component: "ListBox"
description: "Typescript ListBox supports dual list (i.e) reordering of items within the list box and between two list boxes."
---

# Dual list box

The dual list box allows the user to move items between two list boxes by clicking the toolbar buttons. Dual list box can be created by listing items in the
[`toolbarSettings`](../api/list-box/#toolbarsettings) along with the `scope` property.

The following operations can be performed in dual list box,

| Options | Description |
|------|-------------|
| moveUp | Move the selected item in the upward direction within the list box. |
| moveDown | Move the selected item in the downward direction within the list box. |
| moveTo |  Move the selected item to the another list box. |
| moveFrom | Move the selected item from one list box to the another list box. |
| moveAllTo | Move all the items to the another list box. |
| moveAllFrom |  Move all the items from one list box to the another list box. |

The following example illustrates how to move items from `Group A` to `Group B` list box.

{% tab template="list-box/dual-list-box", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html", iframeHeight="500px" %}

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

    // Set the groupA data to the data source.
    dataSource: groupA,

    // Map the appropriate columns to fields property.
    fields: { text: 'Name'},

    // Set the scope of the ListBox.
    scope: '#listbox2',

    // Set the tool settings with set of items.
    toolbarSettings: { items: ['moveUp', 'moveDown', 'moveTo', 'moveFrom', 'moveAllTo', 'moveAllFrom']},

    height: '330px'

});

listObj.appendTo('#listbox1');

listObj = new ListBox({

    // Set the groupB data to the data source.
    dataSource: groupB,

    // Map the appropriate columns to fields property.
    fields: { text: 'Name' },

    height: '330px'

});

listObj.appendTo('#listbox2');

```

{% endtab %}