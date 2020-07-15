---
title: "Form submit to the list box"
component: "ListBox"
description: "TypeScript ListBox component supports form submit to the list box."
---

# Form submit to the list box

In the following code snippet, the value that is in selected state will be sent on form submit.

{% tab template="list-box/form-submit", es5Template="formsubmit", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

import { ListBox } from '@syncfusion/ej2-dropdowns';
import { Button } from '@syncfusion/ej2-buttons';

// define the array of object
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom' },
    { text: 'Bugatti Chiron' },
    { text: 'Bugatti Veyron Super Sport' },
    { text: 'SSC Ultimate Aero' },
    { text: 'Koenigsegg CCR' },
    { text: 'McLaren F1' },
    { text: 'Aston Martin One- 77' },
    { text: 'Jaguar XJ220' },
    { text: 'McLaren P1' },
    { text: 'Ferrari LaFerrari' },
];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: data
});
listObj.appendTo('#listbox');

let button: Button = new Button({ isPrimary: true, content: 'Submit' });
button.appendTo('#btnElement');

```

{% endtab %}