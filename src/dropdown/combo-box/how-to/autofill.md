---
title: "Combo box autofill"
component: "ComboBox"
description: "This section explains how to acheive autofill functionality in combo box control."
---

# Autofill supported with ComboBox

The ComboBox supports the `autofill` behaviour with the help
of [autofill](../../api/combo-box/#autofill) property. Whenever you change the input value,
the ComboBox will autocomplete your data by matching the typed character. Suppose, if no matches
found then, comboBox doesn't suggest any item.

In the following sample, showcase that how to work autofill with ComboBox.

{% tab template="combobox/getting-started", es5Template="autofill", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox({
    //set the data to dataSource property
    dataSource: sportsData,
    // enable the autofill behavior.
    autofill: true,
    // set placeholder to ComboBox input element
    placeholder: "Select a game"
});

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');
```

{% endtab %}
