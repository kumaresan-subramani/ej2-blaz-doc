---
title: "Autocomplete How to show the list items with icons"
component: "AutoComplete"
description: "This section explains how to add icons with autocomplete options."
---

# Show the list items with icons

You can render **icons** to the list items by mapping the
[`iconCss`](../../api/auto-complete/#fields) field. This `iconCss` field
create a span in the list item with mapped class name to allow styling as per your need.

In the following sample, the icon classes are mapped with `iconCss` field.

{% tab template="autocomplete/icon-class", es5Template="basic-icon", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
let sortFormatData: { [key: string]: Object }[] = [
    { Class: 'asc-sort', Type: 'Sort A to Z', Id: '1' },
    { Class: 'dsc-sort', Type: 'Sort Z to A ', Id: '2' },
    { Class: 'filter', Type: 'Filter', Id: '3' },
    { Class: 'clear', Type: 'Clear', Id: '4' }
];

let sortFormat: AutoComplete = new AutoComplete({
    //set the data to dataSource property
    dataSource: sortFormatData,
    // map the icon column to iconCSS field.
    fields: { value: 'Type', iconCss: 'Class' },
    // set placeholder to AutoComplete input element
    placeholder: 'Find a format'
});
sortFormat.appendTo('#atcelement');

```

{% endtab %}
