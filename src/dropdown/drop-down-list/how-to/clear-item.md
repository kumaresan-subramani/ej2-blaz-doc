---
title: "Drop-down list How to clear the list item"
component: "DropDownList"
description: "This section explains on how to clear the selected items of the Syncfusion JavaScript drop-down list control."
---

# Clear the selected item in DropDownList

You can clear the selected item in the below two different ways.

By clicking on the `clear icon` which is shown in DropDownList element, you can clear the selected item in
DropDownList through **interaction**. By using [showClearButton](../../api/drop-down-list/#showclearbutton)
property, you can enable the clear icon in DropDownList element.

Through **programmatic** you can set `null` value to anyone of the index, text or value property to clear the selected item in DropDownList.

The following example demonstrate about how to clear the selected item in DropDownList.

{% tab template="dropdownlist/how-to/clear", es5Template="clear-selectvalue", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Button } from '@syncfusion/ej2-buttons';

// define the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize DropDownList component
let dropDownListObject: DropDownList = new DropDownList({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to DropDownList input element
    placeholder: "Select a game",
    //enable the clear icon
    showClearButton: true
});
// render initialized DropDownList
dropDownListObject.appendTo('#ddlelement');

// Set null value to value property for clear the selected item
document.getElementById('btn').onclick = () => {
  dropDownListObject.value = null;
}

```

{% endtab %}