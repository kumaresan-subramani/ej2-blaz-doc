---
title: "Multiselect How to"
component: "MultiSelect"
description: "This section demonstrates the add an icon in each list item of the Syncfusion JavaScript multiselect control."
---

# Show the list items with icons

You can render **icons** to the list items by mapping the
[iconCss](../../api/multi-select/#fields)
&nbsp;field. This `iconCss` field create a span in the list item with mapped class name
to allow styling as per your need.

In the following sample, icon classes are mapped with `iconCss` field.

{% tab template="multiselect/icon-class", es5Template="icon-howto", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
let sortFormatData: { [key: string]: Object }[] = [
    { class: 'asc-sort', type: 'Sort A to Z', id: '1' },
    { class: 'dsc-sort', type: 'Sort Z to A ', id: '2' },
    { class: 'filter', type: 'Filter', id: '3' },
    { class: 'clear', type: 'Clear', id: '4' }
];

let sortFormat: MultiSelect = new MultiSelect({
    dataSource: sortFormatData,
    // map the icon column to iconCSS field.
    fields: { text: 'type', iconCss: 'class', value: 'id' },
    placeholder: 'Select a format'
});
sortFormat.appendTo('#select');

```

{% endtab %}