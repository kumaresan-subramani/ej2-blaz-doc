---
title: "Multiselect Chip Customization"
component: "MultiSelect"
description: "This section for Syncfusion JavaScript multiselect control demonstrates on how to customize the selected chip element when select."
---

# Chip Customization

The MultiSelect allows the user to customize the selected chip element through the [`tagging`](../api/multi-select/#tagging) event. In that event, you can set the custom classes to chip element via that event argument of `setClass` method.

The following sample demonstrates chip-customization with the MultiSelect component.

{% tab template="multiselect/chip-customization",  es5Template="basic-customization", sourceFiles="app.ts,index.html" %}

```typescript

import { MultiSelect,TaggingEventArgs  } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
 let colorsData: { [key: string]: Object; }[] = [
        { Color: 'Chocolate', Code: '#75523C' },
        { Color: 'CadetBlue', Code: '#3B8289' },
        { Color: 'DarkOrange', Code: '#FF843D' },
        { Color: 'DarkRed', Code: '#CA3832' },
        { Color: 'Fuchsia', Code: '#D44FA3' },
        { Color: 'HotPink', Code: '#F23F82' },
        { Color: 'Indigo', Code: '#2F5D81' },
        { Color: 'LimeGreen', Code: '#4CD242' },
        { Color: 'OrangeRed', Code: '#FE2A00' },
        { Color: 'Tomato', Code: '#FF745C' }
    ];

//initiate the MultiSelect
let msObject: MultiSelect = new MultiSelect({
    // bind the sports Data to datasource property
    dataSource: colorsData,
    // maps the appropriate column to fields property
    fields: { text: 'Color', value: 'Code' },
    // set the value to MultiSelect
    value: ['#75523C', '#4CD242', '#FF745C'],
    //set the placeholder to MultiSelect input
    placeholder:"Select a color",
    // set the type of mode for how to visualized the selected items in input element.
    mode: 'Box',
    // bind the tagging event
    tagging: (e: TaggingEventArgs) => {
            // set the current selected item text as class to chip element.
            e.setClass((e.itemData as any)[msObject.fields.text].toLowerCase());
        }
});
// render initialized multiSelect
msObject.appendTo('#select');

```

{% endtab %}
