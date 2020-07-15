---
title: "Choose a date in range"
component: "DatePicker"
description: "Date picker has `min` and `max` properties which restricts the user from selecting a value out of given min/max date range"
---

# Date Range

DatePicker provides an option to select a date value within a specified range by using the
[`min`](../api/datepicker#min)
and
[`max`](../api/datepicker#max)
properties. Always the min value has to be
lesser than the max value.

When the min and max properties are configured and the selected date value is out-of-range or
invalid, then the model value will be set to `out of range` date value or `null` respectively
with highlighted `error` class to indicates the date is out of range or invalid.

The value property depends on the min/max with respect to [`strictMode`](./strict-mode/) property.

The below example allows selecting a
date within the range from 7th to 27th day in
a month.

{% tab template="datepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",
es5Template="datepicker-range-template" %}

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
let today: Date = new Date();
let currentYear: number = today.getFullYear();
let currentMonth: number = today.getMonth();
let currentDay: number = today.getDate();
// creates a datepicker with min max property
let datepickerObject: DatePicker = new DatePicker({
    //sets the min.
    min: new Date(currentYear, currentMonth, 7),
    //sets the max.
    max: new Date(currentYear, currentMonth, 27),
    //sets the value.
    value: new Date(new Date().setDate(14))
});
datepickerObject.appendTo('#element');

```

{% endtab %}

> If the value of `min` or `max` properties
changed through code behind, then you have to
update the `value` property to set within the
range.