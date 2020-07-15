---
title: "Drop-down list Initialize Tags"
component: "DropDownList"
description: "This section explains the different tags which are used in the initialization of Syncfusion JavaScript drop-down list control."
---

# Initialize Tags

The DropDownList can be initialized on three different tags as described in below.
Though it is initialized in different tags, the UI appearance and built-in features behave in the same way.

## Select element

When a DropDownList is initialized on SELECT element, the list items can be assigned
through the option tag of the HTML select element.

* The nested items are wrapped and grouped based on the `<optgroup>` tag that is available
    within the `<select>` element, by default.
* You can preselect the option by setting the `selected` attribute to an option tag.

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

## UL element

The DropDownList can be initialized through `<UL>` element which contains a collection of `<LI>` element.
The `<LI>` items act as a popup list items of the DropDownList. The inner text of the `<LI>` element
is considered both as text and value fields.

{% tab template="dropdownlist/ul-element",es5Template="ul-element", sourceFiles="app.ts,index.html" %}

```typescript
import { DropDownList } from '@syncfusion/ej2-dropdowns';

    // initialize DropDownList component
    let dropDownListObject: DropDownList = new DropDownList({
        placeholder:"Select a vegetable"
    });

    // render initialized DropDownList
    dropDownListObject.appendTo('#ulElement');
```

{% endtab %}

## Input element

The DropDownList has also be rendered through `<input>` element with an array of either simple or
complex data that is set through
the [dataSource](../api/drop-down-list/#datasource) &nbsp;property.
It can retrieve data from local data sources as well as remote data services.

Detailed information about the data binding with an example is available in:
[Data Binding to DropDownList](./data-binding)