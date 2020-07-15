---
title: "Show tooltip to the list box"
component: "ListBox"
description: "TypeScript ListBox component supports tooltip to the list box."
---

# Show tooltip

Tooltip can be shown for each list box items by customizing it in [`beforeItemRender`](../api/list-box/#beforeitemrender) event.

In the following example, the tooltip can be shown by setting `title` attribute for each `li` element in `beforeItemRender` event.

{% tab template="list-box/getting-started", es5Template="tooltip", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript

import { ListBox, BeforeItemRenderEventArgs } from '@syncfusion/ej2-dropdowns';

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
    beforeItemRender: (args: BeforeItemRenderEventArgs ) => {
        args.element.setAttribute('title', args.element.textContent);
    }
});
listObj.appendTo('#listbox');

```

{% endtab %}