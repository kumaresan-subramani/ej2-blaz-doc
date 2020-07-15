---
title: "Multiselect Grouping"
component: "MultiSelect"
description: "This section for Syncfusion JavaScript multiselect control demonstrates the grouping with individual header and it's header customization."
---

# Grouping

The MultiSelect supports wrapping nested elements into a group based on different categories. The category
of each list item can be mapped through the [groupBy](../api/multi-select/#fields) field in
the data table. The group header is displayed both as inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the popup list with its category value.

In the following sample, vegetables are grouped according on its category using `groupBy` field.

{% tab template="multiselect/basic", es5Template="basic-group" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
//define the data with category
let vegetableData: { [key: string]: Object }[] = [
        { vegetable: 'Cabbage', category: 'Leafy and Salad', id: 'item1' },
        { vegetable: 'Spinach', category: 'Leafy and Salad', id: 'item2' },
        { vegetable: 'Wheat grass', category: 'Leafy and Salad', id: 'item3' },
        { vegetable: 'Yarrow', category: 'Leafy and Salad', id: 'item4' },
        { vegetable: 'Pumpkins', category: 'Leafy and Salad', id: 'item5' },
        { vegetable: 'Chickpea', category: 'Beans', id: 'item6' },
        { vegetable: 'Green bean', category: 'Beans', id: 'item7' },
        { vegetable: 'Horse gram', category: 'Beans', id: 'item8' },
        { vegetable: 'Garlic', category: 'Bulb and Stem', id: 'item9' },
        { vegetable: 'Nopal', category: 'Bulb and Stem', id: 'item10' },
        { vegetable: 'Onion', category: 'Bulb and Stem', id: 'item11' }
    ];
//initiate the MultiSelect
let vegetables: MultiSelect = new MultiSelect({
    //set the grouped data to dataSource property
    dataSource: vegetableData,
    // map the groupBy field with category column
    fields: { groupBy: 'category', text: 'vegetable', value: 'id' },
    // set the placeholder to the MultiSelect input
    placeholder: "Select vegetables",
    // Set the popup list height
    popupHeight: '200px'
});
//render the MultiSelect component
vegetables.appendTo('#select');

```

{% endtab %}

## HTML select

The MultiSelect also supports grouping of list items under specific groups by initiating
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

{% tab template="multiselect/select-element", es5Template="select", sourceFiles="app.ts,index.html" %}

```typescript
import { MultiSelect } from '@syncfusion/ej2-dropdowns';

    // initialize MultiSelect component
    let msObject: MultiSelect = new MultiSelect({
        placeholder:"Select vegetables"
    });

    // render initialized MultiSelect
    msObject.appendTo('#selectElement');
```

{% endtab %}

## Customization

The grouping header is also provided with customization option. This allows custom designing using the [`groupTemplate`](../api/multi-select/#grouptemplate) property for both inline and fixed headers.

## Grouping with CheckBox

Previously, there is no checkbox for group headers. Now, this feature allow to render checkbox in group header to select the group items in single selection. You can enable this feature by setting [`enableGroupCheckBox`](../api/multi-select/#enablegroupcheckbox) property value as **true** and **mode** property as **CheckBox**.

Inject the `CheckBoxSelection` module in the MultiSelect to use the checkbox.

{% tab template="multiselect/basic", es5Template="checkbox-grouping-with-checkbox", sourceFiles="app.ts,index.html" %}

```typescript

import { MultiSelect, CheckBoxSelection } from '@syncfusion/ej2-dropdowns';

MultiSelect.Inject(CheckBoxSelection);

//define the array of complex data
let sportsData: { [key: string]: Object }[] = [
    { vegetable: 'Cabbage', category: 'Leafy and Salad', id: 'item1' },
        { vegetable: 'Spinach', category: 'Leafy and Salad', id: 'item2' },
        { vegetable: 'Wheat grass', category: 'Leafy and Salad', id: 'item3' },
        { vegetable: 'Yarrow', category: 'Leafy and Salad', id: 'item4' },
        { vegetable: 'Pumpkins', category: 'Leafy and Salad', id: 'item5' },
        { vegetable: 'Chickpea', category: 'Beans', id: 'item6' },
        { vegetable: 'Green bean', category: 'Beans', id: 'item7' },
        { vegetable: 'Horse gram', category: 'Beans', id: 'item8' },
        { vegetable: 'Garlic', category: 'Bulb and Stem', id: 'item9' },
        { vegetable: 'Nopal', category: 'Bulb and Stem', id: 'item10' },
        { vegetable: 'Onion', category: 'Bulb and Stem', id: 'item11' }
];

//initiate the MultiSelect
let msObject: MultiSelect = new MultiSelect({
    // bind the sports Data to datasource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { groupBy: 'category', text: 'vegetable', value: 'id' },
    //set the placeholder to MultiSelect input
    placeholder:"Select vegetables",
    // set the type of mode for checkbox to visualized the checkbox added in li element.
    mode: 'CheckBox',
    // set true for enable the selectAll support.
    showSelectAll: true,
    // set value for allowFiltering as true
    allowFiltering: true,
    // set placeholder to filterbar
    filterBarPlaceholder: "Search Vegetables",
    // set true for enableGroupCheckBox property
    enableGroupCheckBox: true
});
//render the component
msObject.appendTo('#select');

```

{% endtab %}

## See Also

* [Group Template support to MultiSelect](./templates/#group-template).