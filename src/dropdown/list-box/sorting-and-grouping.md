---
title: "ListBox sorting and grouping"
component: "ListBox"
description: "Typescript ListBox supports sorting of items in the alphabetical order and group items based on its category."
---

# sorting and grouping

## Sorting

The ListBox supports sorting of available items in the alphabetical order that can be either ascending or descending. This can achieved using
[`sortOrder`](../api/list-box/#sortorder) property. Sort order can be `None`, `Ascending` or `Descending`.

In the following example, the `SortOrder` is set as `Descending`.

{% tab template="list-box/sorting", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

let countryData: { [key: string]: Object }[] = [
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

//initiates the component
let listObj: ListBox = new ListBox({
    dataSource: countryData,
    fields: { text: 'Name' },
    sortOrder: 'Descending'
});


listObj.appendTo('#listbox');

```

{% endtab %}

## Grouping

The ListBox supports to wrap the nested element into a group based on its category. The category of each list item can be mapped with
[`groupBy`](../api/list-box/fieldSettingsModel/#groupby) field in the data table.

In the following example, vegetables are grouped based on its category.

{% tab template="list-box/sorting", es5Template="grouping", isDefaultActive = "true", sourceFiles="app.ts,index.html", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

let vegetableData: { [key: string]: Object }[] = [
    { "Vegetable": "Cabbage", "Category": "Leafy and Salad", "Id": "item1" },
    { "Vegetable": "Spinach", "Category": "Leafy and Salad", "Id": "item2" },
    { "Vegetable": "Wheat grass", "Category": "Leafy and Salad", "Id": "item3" },
    { "Vegetable": "Yarrow", "Category": "Leafy and Salad", "Id": "item4" },
    { "Vegetable": "Pumpkins", "Category": "Leafy and Salad", "Id": "item5" },
    { "Vegetable": "Chickpea", "Category": "Beans", "Id": "item6" },
    { "Vegetable": "Green bean", "Category": "Beans", "Id": "item7" },
    { "Vegetable": "Horse gram", "Category": "Beans", "Id": "item8" },
    { "Vegetable": "Garlic", "Category": "Bulb and Stem", "Id": "item9" },
    { "Vegetable": "Nopal", "Category": "Bulb and Stem", "Id": "item10" },
    { "Vegetable": "Onion", "Category": "Bulb and Stem", "Id": "item11" }
];

//initiates the component
let listObj: ListBox = new ListBox({
    dataSource: vegetableData,

    // Map the appropriate columns to fields property along with groupBy option.
    fields: { groupBy: 'Category', text: 'Vegetable', value: 'Id' }
});


listObj.appendTo('#listbox');

```

{% endtab %}

### HTML element

The ListBox also supports grouping of list items under specific groups by initiating the `<select>` element using  `optgroup`. The nested items are wrapped based on
the `<optgroup>` tag that is presents in the `<select>` element.

{% tab template="list-box/opt-group", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

//initiates the component
let listObj: ListBox = new ListBox({});


listObj.appendTo('#listbox');

```

{% endtab %}

## See Also

* [How to bind the data source to the list box](./getting-started/#binding-data-source)
* [How to initialize the list box](./getting-started/#initialize-the-listbox)
