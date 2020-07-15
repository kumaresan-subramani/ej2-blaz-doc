---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Set the placeholder

The following example demonstrates how to set `placholder` in the DatePicker component.

Using `placeholder` you can display a short hint in the input element.

{% tab template="datepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",
es5Template="datepicker-placeholder-template" %}

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
// creates datepicker with placeholder.
let datepickerObject: DatePicker = new DatePicker({
    // sets the palceholder property.
    placeholder:'Enter date'
});
datepickerObject.appendTo('#element');

```

{% endtab %}