---
title: "Drop-down list How to show the list item with icon"
component: "DropDownList"
description: "This section explains on how to show the list items with icon in the Syncfusion JavaScript drop-down list control."
---

# Show the list items with icons

You can render **icons** to the list items by mapping the
[iconCss](../../api/drop-down-list/#fields)
&nbsp;field. This `iconCss` field create a span in the list item with mapped class name
to allow styling as per your need.

In the following sample, icon classes are mapped with `iconCss` field.

{% tab template="dropdownlist/icon-class", es5Template="basic-icon", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
let sortFormatData: { [key: string]: Object }[] = [
    { Class: 'asc-sort', Type: 'Sort A to Z', Id: '1' },
    { Class: 'dsc-sort', Type: 'Sort Z to A ', Id: '2' },
    { Class: 'filter', Type: 'Filter', Id: '3' },
    { Class: 'clear', Type: 'Clear', Id: '4' }
];

let sortFormat: DropDownList = new DropDownList({
    dataSource: sortFormatData,
    // map the icon column to iconCSS field.
    fields: { text: 'Type', iconCss: 'Class', value: 'Id' },
    placeholder: 'Select a format'
});
sortFormat.appendTo('#ddlelement');

```

{% endtab %}