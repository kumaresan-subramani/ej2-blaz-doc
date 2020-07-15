---
title: "Combo box Grouping"
component: "ComboBox"
description: "This section Syncfusion JavaScript combo box control shows the grouping of suggestions with individual header and it's header customization."
---

# Grouping

The ComboBox supports wrapping nested elements into a group based on different categories. The category
of each list item can be mapped through the [groupBy](../api/combo-box/#fields) &nbsp;field in
the data table. The group header is displayed both as inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the popup list with its category value.

In the following sample, vegetables are grouped according on its category using `groupBy` field.

{% tab template="combobox/basic", es5Template="basic-grouping" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
//define the data with category
let vegetableData: { [key: string]: Object }[] = [
        { Vegetable: 'Chickpea', Category: 'Beans', Id: '1' },
        { Vegetable: 'Green bean', Category: 'Beans', Id: '2' },
        { Vegetable: 'Spinach', Category: 'Leafy and Salad', Id: '3' },
        { Vegetable: 'Horse gram', Category: 'Beans', Id: '4' },
        { Vegetable: 'Cabbage', Category: 'Leafy and Salad', Id: '5' },
        { Vegetable: 'Wheat grass', Category: 'Leafy and Salad', Id: '6' },
        { Vegetable: 'Yarrow', Category: 'Leafy and Salad', Id: '7' }
    ];
//initiate the ComboBox
let vegetables: ComboBox = new ComboBox({
    //set the grouped data to dataSource property
    dataSource: vegetableData,
    // map the groupBy field with Category column
    fields: { groupBy: 'Category', text: 'Vegetable', value: 'Id' },
    // set the placeholder to the ComboBox input
    placeholder: "Select a vegetable",
    // Set the popup list height
    popupHeight: '200px'
});
//render the ComboBox component
vegetables.appendTo('#comboelement');

```

{% endtab %}

## HTML select

The ComboBox also supports grouping of list items under specific groups by initiating
the `<select>` element using  `optgroup`. The nested items are wrapped based on
the `<optgroup>` tag that is presents in the `<select>` element

```html
    <select id="selectElement">
        <optgroup label="Beans">
            <option value="1">Chickpea</option>
            <option value="2">Green bean</option>
            <option value="3" selected="selected">Horse gram</option>
        </optgroup>
        <optgroup label="Leafy and Salad">
            <option value="4">Spinach</option>
            <option value="5">Cabbage</option>
            <option value="6">Wheat grass</option>
            <option value="7">Yarrow</option>
        </optgroup>
    </select>
```

{% tab template="combobox/select-element", es5Template="select-element", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

    // initialize ComboBox component
    let ComboBoxObject: ComboBox = new ComboBox({
        placeholder:"Select a vegetable",
        popupHeight: "200px"
    });

    // render initialized ComboBox
    ComboBoxObject.appendTo('#selectElement');
```

{% endtab %}

## Customization

The grouping header is also provided with customization option. This allows custom designing using the [`groupTemplate`](../api/combo-box/#grouptemplate) property for both inline and fixed headers.

## See Also

* [Group Template support to ComboBox](./templates/#group-template).
