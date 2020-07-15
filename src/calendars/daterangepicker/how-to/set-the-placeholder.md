---
title: "How To"
component: "DateRangePicker"
description: "Miscellaneous aspects of customizing the date range picker"
---

# Set the placeholder

The following example demonstrates how to set [`placeholder`](../../api/daterangepicker#placeholder) in the DateRangePicker control.

Using `placeholder` you can display a short hint in the input element.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="daterangepicker-placeholder-template"%}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates DateRangePicker with placeholder.
let daterangeObject: DateRangePicker = new DateRangePicker({
    // sets the placeholder property.
    placeholder:'Select a range'
});
daterangeObject.appendTo('#element');

```

{% endtab %}