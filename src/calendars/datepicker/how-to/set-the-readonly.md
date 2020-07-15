---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Set the readonly

The following example demonstrates how to set `readonly` in DatePicker component.
You can achieve this by using [`readonly`](../../api/datepicker#readonly) property.

{% tab template="datepicker/getting-started" , sourceFiles="app.ts,index.html"
,es5Template="datepicker-readonly-template" %}

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
// creates datepicker with readonly.
let datepickerObject: DatePicker = new DatePicker({
    // sets the readonly.
    readonly:true,
    // sets the value.
    value:new Date(),
    // sets the palceholder property.
    placeholder:'Enter date'
});
datepickerObject.appendTo('#element');

```

{% endtab %}
