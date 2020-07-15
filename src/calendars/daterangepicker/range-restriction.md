---
title: "Range Restriction"
control: "DateRangePicker"
description: "Date range picker has `min` and `max` properties which restricts the user from selecting a date range value out of given min/max date range"
---

# Range Restriction

Range selection in a date range picker can be made-to-order with desire restrictions based on the application needs.

## Restrict the range within a range

You can restrict the minimum and maximum date that can be allowed as start and end date in a range selection with the help of [`min`](../api/daterangepicker#min), [`max`](../api/daterangepicker#max) properties.
* `min` – sets the minimum date that can be selected as startDate.
* `max` – sets the maximum date that can be selected as endDate.

In the following sample, you can select a range from 15th day of this month to 15th day of next month.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html", es5Template="daterangepicker-rangerestriction-template" %}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
let today: Date = new Date();
let currentYear: number = today.getFullYear();
let currentMonth: number = today.getMonth();
let currentDay: number = today.getDate();
// creates a daterangepicker with min max property
let daterangeObject: DateRangePicker = new DateRangePicker({
    //sets the min.
    min: new Date(currentYear, currentMonth, 15),
    //sets the max.
    max: new Date(currentYear, currentMonth+1, 15),
    placeholder:"Select a Range"

});
daterangeObject.appendTo('#element');

```

{% endtab %}

> If the value of `min` or `max` properties
changed through code behind, then you have to
update the `start date`, `end date` property to set within the
range. Or else , if the `start` and `end` date is out of specified date range, a validation error class will
be appended to the input element. If `strictMode` is enabled, and both the start, end date is lesser than the
min date then start and end date will be updated with `min` date. If both the start and end date is higher
than the max date then start and end date will be updated with `max` date. Or else, if startDate is less than
`min` date, startDate will be updated with `min` date or if endDate is greater than `max` date, endDate will be updated with the `max` date.

## Range span

Days span between ranges can be limited in order to avoid excess or less days selection towards the required days in a range.
In this, minimum and maximum span allowed within the date range can be customized by [`minDays`](../api/daterangepicker#mindays) and [`maxDays`](../api/daterangepicker#maxdays) properties.
* minDays- Sets the minimum number of days between start and end date.
* maxDays- Sets the maximum number of days between start and end date.
In the following sample, the range selection should be greater than 3 days and less than 8 days else it will not set.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="daterangepicker-rangespan-template"%}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
let today: Date = new Date();
let currentYear: number = today.getFullYear();
let currentMonth: number = today.getMonth();
let currentDay: number = today.getDate();
// creates a daterangepicker with min max property
let daterangeObject: DateRangePicker = new DateRangePicker({
    //sets the minimum number of days
    minDays: 4,
    //sets the maximum number of days
    maxDays: 7,
    placeholder:"Select a Range"
});
daterangeObject.appendTo('#element');

```

{% endtab %}

## Strict mode

DateRangePicker provides an option to limit the user towards entering the valid date.  With strict mode, you can set only the valid date. If any invalid range is specified, the date range value resets to previous value. This restriction can be availed by enabling [`strictMode`](../api/daterangepicker#strictmode) property as true.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="daterangepicker-strictmode-template"%}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates a daterangepicker in strict mode
let daterangeObject: DateRangePicker = new DateRangePicker({
        //enabling strict mode
        strictMode: true, placeholder:"Select a Range"
});
daterangeObject.appendTo('#element');

```

{% endtab %}
