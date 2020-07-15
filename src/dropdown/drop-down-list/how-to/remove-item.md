---
title: "Drop-down list How to remove list item"
component: "DropDownList"
description: "This section explains on how to remove the list item of the Syncfusion JavaScript drop-down list control."
---

# Remove an item from DropDownList

The following example demonstrate about how to remove an item from DropDownList.

{% tab template="dropdownlist/how-to/remove_item", es5Template="removeitem", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';

//define the array of complex data
let sportsData: { [key: string]: Object }[] = [
    { Id: 'game1', Game: 'Badminton' },
    { Id: 'game2', Game: 'Football' },
    { Id: 'game3', Game: 'Tennis' }
];

//initiate the DropDownList
let dropDownListObject: DropDownList = new DropDownList({
    // bind the sports Data to datasource property
    dataSource: sportsData,
    // maps the appropriate column to fields property
    fields: { text: 'Game', value: 'Id' },
    //set the placeholder to DropDownList input
    placeholder:"Select a game"
});
//render the componen
dropDownListObject.appendTo('#ddlelement');

document.getElementById('first').onclick = () => {
    // create DropDownList object
    let obj: any = document.getElementById('ddlelement');
    if (obj.ej2_instances[0].list) {
        // Remove the selected value if 0th index selected
        if (dropDownListObject.index === 0) {
            dropDownListObject.value = null;
            dropDownListObject.dataBind();
        }
        // remove first item in list
        (obj.ej2_instances[0].list.querySelectorAll('li')[0]).remove();
        if (!obj.ej2_instances[0].list.querySelectorAll('li')[0]) {
            dropDownListObject.dataSource = [];
            // enable the nodata template when no data source is empty.
            obj.ej2_instances[0].list.classList.add('e-nodata');
        }
    } else {
        // remove first item in list
        dropDownListObject.dataSource.splice(0, 1);
    }
}

```

{% endtab %}