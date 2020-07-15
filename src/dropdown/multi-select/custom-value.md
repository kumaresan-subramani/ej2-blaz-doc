---
title: "Multiselect Custom value"
component: "MultiSelect"
description: "This section for Syncfusion JavaScript multiselect control demonstrates the addition of a new value that is not present in the predefined list."
---

# CustomValue

The MultiSelect allows user to add a new non-present option to the component value when [`allowCustomValue`](../api/multi-select/#allowcustomvalue) is enabled. while selecting the new custom value [`customValueSelection`](../api/multi-select/#customvalueselection) event will be triggered.

The following sample demonstrates configuration of custom value support with the MultiSelect component.

{% tab template="multiselect/basic",  es5Template="basic-customvalue", sourceFiles="app.ts,index.html" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let sportsData: { [key: string]: Object }[] = [
    { id: 'game1', sports: 'Badminton' },
    { id: 'game2', sports: 'Football' },
    { id: 'game3', sports: 'Tennis' }
];

//initiate the MultiSelect
let msObject: MultiSelect = new MultiSelect({
    // bind the sports Data to datasource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { text: 'sports', value: 'id' },
    //set the placeholder to MultiSelect input
    placeholder:"Select games",
    //enable custom Value option with multislect
    allowCustomValue:true
});
// render initialized multiSelect
msObject.appendTo('#select');

```

{% endtab %}
