---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Open the DatePicker popup upon input click

To open the DatePicker popup upon input click by using `show` method in the `focus` event.

The following example demonstrates how to open the DatePicker popup upon focus the input.

{% tab template="datepicker/open-popup" , sourceFiles="app.ts,index.html",
es5Template="datepicker-open-popup-template" %}

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
// creates datepicker component
let datepickerObject: DatePicker = new DatePicker({
    focus: function () {
        // To open the popup upon input click
        datepickerObject.show();
    },
    // sets the palceholder property.
    placeholder: 'Enter date'
});
datepickerObject.appendTo('#element');
```

{% endtab %}
