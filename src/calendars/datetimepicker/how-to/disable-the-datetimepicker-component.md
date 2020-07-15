---
title: "How To"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the date time picker"
---

# Disable the component

To disable the DateTimePicker, use its
[`enable`](../../api/datetimepicker#enabled)
property to `false`.

{% tab template="datetimepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="datetimepicker-disabled-template"%}

```typescript

import { DateTimePicker } from '@syncfusion/ej2-calendars';
// creates datetimepicker with enabled property
let datetimeObject: DateTimePicker = new DateTimePicker({
    // sets the enabled as false
    enabled:false, placeholder:"Select a date and time"
});
datetimeObject.appendTo('#element');

```

{% endtab %}