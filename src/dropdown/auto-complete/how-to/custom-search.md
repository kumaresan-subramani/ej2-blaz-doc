---
title: "Autocomplete custom highlight search"
component: "AutoComplete"
description: "This section explains custom highlight search of autocomplete control."
---

# Custom highlight search

The AutoComplete has built-in support to highlight the searched characters on suggested list items when
enabled the [`highlight`](../../api/auto-complete/#highlight) property.

In the below sample, to customize the matched character in suggestion list by `e-highlight` class.

{% tab template="autocomplete/highlight", es5Template="highlight-search", sourceFiles="app.ts,index.html,style.css" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let searchData: { [key: string]: Object; }[] = [
    { Name: 'Australia', Code: 'AU' },
    { Name: 'Bermuda', Code: 'BM' },
    { Name: 'Canada', Code: 'CA' },
    { Name: 'Cameroon', Code: 'CM' },
    { Name: 'Denmark', Code: 'DK' },
    { Name: 'France', Code: 'FR' },
    { Name: 'Finland', Code: 'FI' },
    { Name: 'Germany', Code: 'DE' },
    { Name: 'Greenland', Code: 'GL' },
    { Name: 'Hong Kong', Code: 'HK' },
    { Name: 'India', Code: 'IN' },
    { Name: 'Italy', Code: 'IT' },
    { Name: 'Japan', Code: 'JP' },
    { Name: 'Mexico', Code: 'MX' },
    { Name: 'Norway', Code: 'NO' },
    { Name: 'Poland', Code: 'PL' },
    { Name: 'Switzerland', Code: 'CH' },
    { Name: 'United Kingdom', Code: 'GB' },
    { Name: 'United States', Code: 'US' }];

//initiates the component
let atcObject: AutoComplete = new AutoComplete({
    // bind the country data to dataSource property
    dataSource: searchData,
    // maps the appropriate column to fields property
    fields: { value: "Name" },
    //set the placeholder to AutoComplete input
    placeholder: "Find a country",
     //enable the highlight property to highlight the matched character in suggestion list
    highlight: true
});
atcObject.appendTo('#atcelement');

```

{% endtab %}