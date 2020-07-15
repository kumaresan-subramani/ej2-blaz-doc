---
title: "Autocomplete Grouping"
component: "AutoComplete"
description: "This section for Syncfusion JavaScript autocomplete control explains the grouping of suggestions with individual header and it's header customization."
---

# Grouping

The AutoComplete supports wrapping nested elements into a group based on different categories. The
category of each list item can be mapped through the
[groupBy](../api/auto-complete/#fields) field in the data table. The group
header is displayed as both inline and fixed headers. The fixed group header content
is updated dynamically on scrolling the suggestion list with its category value.

In the following sample, vegetables are grouped according on its category using `groupBy` field.

{% tab template="autocomplete/basic", es5Template="basic-grouping" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
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
//initiate the AutoComplete
let vegetables: AutoComplete = new AutoComplete({
    //set the grouped data to dataSource property
    dataSource: vegetableData,
    // map the groupBy field with Category column
    fields: { groupBy: 'Category', value: 'Vegetable' },
    // set the placeholder to the AutoComplete input
    placeholder: "Find a vegetable"
});
//render the AutoComplete component
vegetables.appendTo('#atcelement');

```

{% endtab %}

## Customization

The grouping header is also provided with customization option. This allows custom designing
using the
[groupTemplate](../api/auto-complete/#grouptemplate) property for both inline and
fixed headers as referred here:

## See Also

* [Group Template support to AutoComplete](./templates/#group-template).