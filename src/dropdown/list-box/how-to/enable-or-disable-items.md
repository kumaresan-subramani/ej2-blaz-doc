---
title: "Enable or disable items in list box"
component: "ListBox"
description: "TypeScript ListBox component supports customization of menu items so that the items can be enabled or disabled."
---

# Enable or disable items

To enable or disable items in the list box, [`enableItems`](../api/list-box/#enableitems) method can be used. In the following example, the `Bugatti Veyron Super Sport` and `SSC Ultimate Aero` items are disabled by default and by clicking `Enable Items` buttons, the disabled items will be enabled.

{% tab template="list-box/enable-items", es5Template="enableitems", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';

// define the array of object
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02' },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04' },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' }
];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: data,
    created: () => {
        listObj.enableItems(['Bugatti Veyron Super Sport', 'SSC Ultimate Aero'], false);
    }
});
listObj.appendTo('#listbox');

document.getElementById('enableitem').onclick = () => {
    listObj.enableItems(['Bugatti Veyron Super Sport', 'SSC Ultimate Aero']);
}

```

{% endtab %}