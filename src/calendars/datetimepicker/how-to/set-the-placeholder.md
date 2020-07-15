---
title: "How To"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the date time picker"
---

# Set the placeholder

The following example demonstrates how to set [`placeholder`](../../api/datetimepicker#placeholder) in the DateTimePicker component.

Using `placeholder` you can display a short hint in the input element.

{% tab template="datetimepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="datetimepicker-placeholder-template"%}

```typescript

import { DateTimePicker } from '@syncfusion/ej2-calendars';
// creates DateTimePicker with placeholder.
let datetimeObject: DateTimePicker = new DateTimePicker({
    // sets the placeholder property.
    placeholder:'Select a date and time'
});
datetimeObject.appendTo('#element');

```

{% endtab %}