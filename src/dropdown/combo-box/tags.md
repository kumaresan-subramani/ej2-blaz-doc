---
title: "Combo box Initialize Tags"
component: "ComboBox"
description: "This section explains the different tags which are used in the initialization of the Syncfusion JavaScript combo box control."
---

# Initialize Tags

The ComboBox can be initialized on three different tags as described in below.
Though it is initialized in different tags, the UI appearance and built-in features behave in the same way.

## Select element

When a ComboBox is initialized on SELECT element, the list items can be assigned
through the option tag of the HTML select element.

* The nested items are wrapped and grouped based on the `<optgroup>` tag that is available
    within the `<select>` element, by default.
* You can preselect the option by setting the `selected` attribute to an option tag.

{% tab template="combobox/select-element",es5Template="select-element", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

    // initialize ComboBox component
    let comboBoxObject: ComboBox = new ComboBox({
        placeholder: "Select a vegetable",
        popupHeight: "200px"
    });

    // render initialized ComboBox
    comboBoxObject.appendTo('#selectElement');
```

{% endtab %}

## UL element

The ComboBox can be initialized through `<UL>` element which contains a collection of `<LI>` element.
The `<LI>` items act as a popup list items of the ComboBox. The inner text of the `<LI>` element
is considered both as text and value fields.

{% tab template="combobox/ul-element", es5Template="ul-element", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

    // initialize ComboBox component
    let comboBoxObject: ComboBox = new ComboBox({
        placeholder:"Select a vegetable"
    });

    // render initialized ComboBox
    comboBoxObject.appendTo('#ulElement');
```

{% endtab %}

## Input element

The ComboBox has also be rendered through `<input>` element with an array of either simple or
complex data that is set through the [dataSource](../api/combo-box/#datasource) &nbsp;property.
It can retrieve data from local data sources as well as remote data services.

Detailed information about the data binding with an example is available in:
[Data Binding to ComboBox](./data-binding)