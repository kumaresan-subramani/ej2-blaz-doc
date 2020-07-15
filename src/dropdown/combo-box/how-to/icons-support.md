---
title: "Combo box How to show the list items with icons"
component: "ComboBox"
description: "This section explains how to add icons with combo box options."
---

# Show the list items with icons

You can render **icons** to the list items by mapping the
[iconCss](../../api/combo-box/#fields)
&nbsp;field. This `iconCss` field create a span in the list item with mapped class name
to allow styling as per your need.

In the following sample, icon classes are mapped with `iconCss` field.

{% tab template="combobox/icon-class", es5Template="basic-icon", sourceFiles ='app.ts,styles.css' %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
let sortFormatData: { [key: string]: Object }[] = [
    { class: 'asc-sort', type: 'Sort A to Z', id: '1' },
    { class: 'dsc-sort', type: 'Sort Z to A ', id: '2' },
    { class: 'filter', type: 'Filter', id: '3' },
    { class: 'clear', type: 'Clear', id: '4' }
];

let sortFormat: ComboBox = new ComboBox({
    dataSource: sortFormatData,
    // map the icon column to iconCSS field.
    fields: { text: 'type', iconCss: 'class', value: 'id' },
    placeholder: 'Select a format'
});
sortFormat.appendTo('#comboelement');

```

{% endtab %}