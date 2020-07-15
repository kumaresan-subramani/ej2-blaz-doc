---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Disabled State

To disable the DatePicker, use its
[`enable`](../../api/datepicker#enabled)
property.

The following example demonstrates the DatePicker in
a disabled state.

{% tab template="datepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",
es5Template="datepicker-disabled-template" %}

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
// creates datepicker with enabled property
let datepickerObject: DatePicker = new DatePicker({
    // sets the enabled
    enabled:false
});
datepickerObject.appendTo('#element');

```

{% endtab %}