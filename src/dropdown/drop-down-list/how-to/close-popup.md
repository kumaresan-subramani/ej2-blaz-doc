---
title: "Drop-down list How to close popup on scroll"
component: "DropDownList"
description: "This section explains on how to close popup on scroll in the Syncfusion JavaScript drop-down list control."
---

# Close the popup on scroll

By using the `hidePopup` method in DropDownList, you can close the popup on scroll when triggered the windows scroll event.

The following example demonstrate about how to close the popup on scroll.

{% tab template="dropdownlist/how-to/close_on_scroll", es5Template="close-onscroll", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';

// define the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize DropDownList component
let dropDownListObject: DropDownList = new DropDownList({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to DropDownList input element
    placeholder: "Select a game"
});

// render initialized DropDownList
dropDownListObject.appendTo('#ddlelement');

// bind the onscroll event to window
window.onscroll = () => {
  dropDownListObject.hidePopup();
}

```

{% endtab %}