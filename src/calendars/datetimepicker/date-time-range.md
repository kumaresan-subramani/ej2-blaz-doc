---
title: "Date Time Range"
component: "DateTimePicker"
description: "Date time picker has `min` and `max` properties which restricts the user from selecting a value out of given min/max datetime range"
---

# DateTime Range

DateTimePicker provides an option to select a date and time value within a specified range by using the
[`min`](../api/datetimepicker#min)
and
[`max`](../api/datetimepicker#max)
properties. Always the min value has to be
lesser than the max value.

When the min and max properties are configured and the selected datetime value is out-of-range
or invalid, then the model value will be set to `out of range` datetime value or `null`
respectively with highlighted `error` class to indicates the datetime is out of range or invalid.

The value property depends
on the min/max with respect to [`strictMode`](../strict-mode.html) property.

The below example allows selecting a
date within the range from 7th to 27th day in
a month.

{% tab template="datetimepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",
es5Template="datetimepicker-range-template" %}

```typescript

import { DateTimePicker } from '@syncfusion/ej2-calendars';
let today: Date = new Date();
let currentYear: number = today.getFullYear();
let currentMonth: number = today.getMonth();
let currentDay: number = today.getDate();
let currentHour: number = today.getHours();
let currentMinute: number = today.getMinutes();
let currentSecond: number = today.getSeconds();
// creates a datetimepicker with min max property
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    //sets the min.
    min: new Date(currentYear, currentMonth, 7, 0, 0, 0),
    //sets the max.
    max: new Date(currentYear, currentMonth, 27,currentHour,currentMinute,currentSecond),
    //sets the value.
    value: new Date(new Date().setDate(14))
});
datetimepickerObject.appendTo('#element');

```

{% endtab %}

> If the value of `min` or `max` properties
changed through code behind, then you have to
update the `value` property to set within the
range.