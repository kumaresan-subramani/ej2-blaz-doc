---
title: "Drop-down list Grouping"
component: "DropDownList"
description: "This section for Syncfusion JavaScript drop-down list control shows the grouping with individual header and it's header customization."
---

# Grouping

The DropDownList supports wrapping nested elements into a group based on different categories. The category
of each list item can be mapped through the [groupBy](../api/drop-down-list/#fields) field in
the data table. The group header is displayed both as inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the popup list with its category value.

In the following sample, vegetables are grouped according on its category using `groupBy` field.

{% tab template="dropdownlist/basic", es5Template="basic-grouping" %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
//define the data with category
let vegetableData: { [key: string]: Object }[] = [
        { Vegetable: 'Cabbage', Category: 'Leafy and Salad', Id: 'item1' },
        { Vegetable: 'Spinach', Category: 'Leafy and Salad', Id: 'item2' },
        { Vegetable: 'Wheat grass', Category: 'Leafy and Salad', Id: 'item3' },
        { Vegetable: 'Yarrow', Category: 'Leafy and Salad', Id: 'item4' },
        { Vegetable: 'Pumpkins', Category: 'Leafy and Salad', Id: 'item5' },
        { Vegetable: 'Chickpea', Category: 'Beans', Id: 'item6' },
        { Vegetable: 'Green bean', Category: 'Beans', Id: 'item7' },
        { Vegetable: 'Horse gram', Category: 'Beans', Id: 'item8' },
        { Vegetable: 'Garlic', Category: 'Bulb and Stem', Id: 'item9' },
        { Vegetable: 'Nopal', Category: 'Bulb and Stem', Id: 'item10' },
        { Vegetable: 'Onion', Category: 'Bulb and Stem', Id: 'item11' }
    ];
//initiate the DropDownList
let vegetables: DropDownList = new DropDownList({
    //set the grouped data to dataSource property
    dataSource: vegetableData,
    // map the groupBy field with Category column
    fields: { groupBy: 'Category', text: 'Vegetable', value: 'Id' },
    // set the placeholder to the DropDownList input
    placeholder: "Select a vegetable",
    // Set the popup list height
    popupHeight: '200px'
});
//render the DropDownList component
vegetables.appendTo('#ddlelement');

```

{% endtab %}

## HTML select

The DropDownList also supports grouping of list items under specific groups by initiating
the `<select>` element using  `optgroup`. The nested items are wrapped based on
the `<optgroup>` tag that is presents in the `<select>` element

```html
    <select id="selectElement">
        <optgroup label="Beans">
            <option value="1">Chickpea</option>
            <option value="2">Green bean</option>
            <option value="3">Horse gram</option>
        </optgroup>
        <optgroup label="Leafy and Salad">
            <option value="4">Spinach</option>
            <option value="5" selected="selected">Cabbage</option>
            <option value="6">Wheat grass</option>
        </optgroup>
    </select>
```

{% tab template="dropdownlist/select-element",es5Template="select-element", sourceFiles="app.ts,index.html" %}

```typescript
import { DropDownList } from '@syncfusion/ej2-dropdowns';

    // initialize DropDownList component
    let dropDownListObject: DropDownList = new DropDownList({
        placeholder:"Select a vegetable"
    });

    // render initialized DropDownList
    dropDownListObject.appendTo('#selectElement');
```

{% endtab %}

## Customization

The grouping header is also provided with customization option. This allows custom designing using the [`groupTemplate`](../api/drop-down-list/#grouptemplate) property for both inline and fixed headers.

## See Also

* [Group Template support to DropDownList](./templates/#group-template).
* [How to disable the fixed group header](./how-to/group-header/)