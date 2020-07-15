---
title: "Date Range"
component: "Calendar"
description: "Calendar has `min` and `max` properties which restricts the user from selecting a value out of given min/max date range"
---

# Date Range

Calendar provides an option to select a date value within a specified range by defining
the [`min`](../api/calendar#min) and [`max`](../api/calendar#max) properties.
The min date should always be lesser than the max date.
If the value of `min` or `max` properties are changed through code behind, then update the `value` property to
be set within the specified range, or else, if the value is out of specified date range and less than `min`
date, value property will be updated with min date or the value is higher than max date, value property will
be updated with `max` date.

The following example allows you to select a date within the range of 7th to 27th days in a month.

{% tab template="calendar/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css" ,es5Template="calendar-range-template"%}

```typescript
import { Calendar, ChangedEventArgs } from '@syncfusion/ej2-calendars';
//Creates a Calendar with min and max properties.
let today: Date = new Date();
let currentYear: number = today.getFullYear();
let currentMonth: number = today.getMonth();
let currentDay: number = today.getDate();
let calendarObject: Calendar = new Calendar({
    //sets the min date
    min: new Date(currentYear, currentMonth, 7),
    //sets the max date
    max: new Date(currentYear, currentMonth, 27),
    //sets the value
    value: new Date(new Date().setDate(14))
});
calendarObject.appendTo('#element');
```

{% endtab %}