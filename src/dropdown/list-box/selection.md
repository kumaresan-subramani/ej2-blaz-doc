---
title: "ListBox selection"
component: "ListBox"
description: "Typescript ListBox supports selection of single item or multiple item, and checkbox selection which supports selection of more than one items."
---

# Selection

The ListBox provides support to select an item or a group of item by mouse or keyboard action. There are two selection modes available in list box,

* Single -  To select single item in the list box.
* Multiple -  To select multiple items in the list box.

> On selection of each list box item, [`select`](../api/list-box/#select) event is triggered.

## Single selection

To enable single selection in the list box, [`mode`](../api/list-box/selectionSettingsModel/#mode) should be set as `Single` in [`selectionSettings`](../api/list-box/#selectionsettings) property.

{% tab template="list-box/getting-started", es5Template="singleselection", isDefaultActive = "true", sourceFiles="app.ts,index.html", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

// define the array of object
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom' },
    { text: 'Bugatti Chiron' },
    { text: 'Bugatti Veyron Super Sport' },
    { text: 'SSC Ultimate Aero'},
    { text: 'Koenigsegg CCR'},
    { text: 'McLaren F1' },
    { text: 'Aston Martin One- 77' },
    { text: 'Jaguar XJ220' },
    { text: 'McLaren P1' },
    { text: 'Ferrari LaFerrari' }
];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: data,
    selectionSettings: {
        mode: 'Single'
    }
});
listObj.appendTo('#listbox');

```

{% endtab %}

## Multiple selection

To enable multiple selection in the list box, `mode` should be set as `Multiple` in `selectionSettings` property.

To select multiple items, use the SHIFT, CTRL, and arrow keys to make selections.

> By default, the selection mode is set as `Multiple`.

{% tab template="list-box/getting-started", es5Template="multipleselection", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

// define the array of object
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom'},
    { text: 'Bugatti Chiron' },
    { text: 'Bugatti Veyron Super Sport' },
    { text: 'SSC Ultimate Aero' },
    { text: 'Koenigsegg CCR' },
    { text: 'McLaren F1' },
    { text: 'Aston Martin One- 77' },
    { text: 'Jaguar XJ220' },
    { text: 'McLaren P1' },
    { text: 'Ferrari LaFerrari' }
];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: data,
    selectionSettings: {
        mode: 'Multiple'
    }
});
listObj.appendTo('#listbox');

```

{% endtab %}

### Checkbox selection

The ListBox supports checkbox in default and grouped list box which is used to select multiple items. CheckBox selection can be enabled by injecting `CheckBoxSelection` module and also [`showCheckBox`](../api/list-box/selectionSettingsModel/#showcheckbox) property should be set as `true`.

#### Select All

To select all the items in the list box, [`showSelectAll`](../api/list-box/selectionSettingsModel/#showselectall) should be set as `true`.

{% tab template="list-box/getting-started", es5Template="selectall", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox, CheckBoxSelection } from '@syncfusion/ej2-dropdowns';

ListBox.Inject(CheckBoxSelection);

// define the array of object
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom'},
    { text: 'Bugatti Chiron' },
    { text: 'Bugatti Veyron Super Sport' },
    { text: 'SSC Ultimate Aero' },
    { text: 'Koenigsegg CCR' },
    { text: 'McLaren F1' },
    { text: 'Aston Martin One- 77' },
    { text: 'Jaguar XJ220' },
    { text: 'McLaren P1' },
    { text: 'Ferrari LaFerrari' }
];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: data,
    selectionSettings: {
       showCheckbox: true,
       showSelectAll: true
    }
});
listObj.appendTo('#listbox');

```

{% endtab %}

> To select all the items in the list box, [`selectAll`](../api/list-box/#selectall) method can also be used.

## See Also

* [How to select items in list box](./icons-and-templates/#Select-items-to-the-list-box)