---
title: "Select items to the list box"
component: "ListBox"
description: "TypeScript ListBox component supports select of items to the list box."
---

# Select items to the list box

In the following example, `Bugatti Chiron` is selected using [`selectItems`](../api/list-box/#selectitems) method.

{% tab template="list-box/select-items", es5Template="selectitems", isDefaultActive = "true", sourceFiles="app.ts,index.html", iframeHeight="500px" %}

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
    created: () => {
        listObj.selectItems(['Bugatti Chiron'])
    }
});
listObj.appendTo('#listbox');

```

{% endtab %}