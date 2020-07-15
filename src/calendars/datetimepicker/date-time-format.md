---
title: "DateTime Format"
component: "DateTimePicker"
description: "Date time picker supports to format date object into specific string format to simplify the date and time representation. It adapts to any culture specific date and time formats when it is globalized."
---

# DateTime Format

DateTime format is a way of representing the date and time value in different string format in the textbox.

By default, the DateTimePicker's format is based on the culture. You can also set the own
custom format by using the
[`format`](../api/datetimepicker#format)
property.

> Once the format property has been defined it will be common to all the cultures.

To know more about the date format standards, refer to the
[Internationalization Date Time Format](http://ej2.syncfusion.com/documentation/base/internationalization/) section.

The following example demonstrates the DateTimePicker with the custom format (`yyyy-MM-dd hh:mm`).

{% tab template="datetimepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",es5Template="datetimepicker-format-template"%}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
// creates a DatePicker component with custom format.
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    value: new Date(),
    // sets the format.
    format: 'yyyy-MM-dd hh:mm'
});
datetimepickerObject.appendTo('#element');
```

{% endtab %}