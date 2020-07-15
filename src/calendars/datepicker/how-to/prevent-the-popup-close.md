---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Prevent the popup close

To prevent the DatePicker popup from closing, use the
preventDefault method from the
`PreventableEventArgs`.

The following example demonstrates how to prevent the popup from closing.

{% tab template="datepicker/getting-started" , sourceFiles="app.ts,index.html",
es5Template="datepicker-preventpopup-template" %}

```typescript

import { DatePicker, PreventableEventArgs } from '@syncfusion/ej2-calendars';
// creates datepicker with readonly.
let datepickerObject: DatePicker = new DatePicker({
    close: function (args: PreventableEventArgs) {
        // prevent the popup close
        args.preventDefault();
    },
    // sets the palceholder property.
    placeholder: 'Enter date'
});
datepickerObject.appendTo('#element');
// open the datepicker popup
datepickerObject.show();

```

{% endtab %}
