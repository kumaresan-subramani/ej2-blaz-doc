---
title: "Drop-down list How to add list item"
component: "DropDownList"
description: "This section explains on how to add list item to the Syncfusion JavaScript drop-down list control."
---

# Add item in between in DropDownList

You can add item in between based on item [index](../../api/drop-down-list/#index). If you add new item without item index, item will be added as last item in list.

The following example demonstrate how to add item in between in DropDownList.

{% tab template="dropdownlist/how-to/add_item", es5Template="additem", sourceFiles ='app.ts,index.html,styles.css' %}

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
//render the component
dropDownListObject.appendTo('#ddlelement');

// add item at first
document.getElementById('first').onclick = () => {
  dropDownListObject.addItem({Id: 'game0', Game: 'Hockey'}, 0);
}

// add item in between
document.getElementById('between').onclick = () => {
  dropDownListObject.addItem({Id: 'game4', Game: 'Golf'}, 2);
}

// add item at last
document.getElementById('last').onclick = () => {
  dropDownListObject.addItem({Id: 'game5', Game: 'Cricket'});
}

```

{% endtab %}