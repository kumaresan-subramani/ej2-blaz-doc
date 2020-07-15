---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Select a sequence of dates in Calendar

The following example demonstrates how to select the week dates of chosen date in the Calendar using [`values`](../../api/calendar#values) property, when [`multiSelection`](../../api/calendar#ismultiselection) property is enabled. Methods of Moment.js is used in this sample for calculating the start and end of week from the selected date.

{% tab template="calendar/how-to-multiselect", sourceFiles="app.ts,index.html,styles.css",es5Template="calendar-multiselect-template" %}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
import moment from "moment";

/*Initialize the calender component*/
let calendar: Calendar = new Calendar({
    isMultiSelection: true,
    change: onChange
});
calendar.appendTo('#calendar');

/*selected current week dates when click the button*/
document.getElementById('workweek').addEventListener('click', function () {
    if (calendar.element.classList.contains('week')) {
        calendar.element.classList.remove('week')
    }
    calendar.element.classList.add('workweek');
});

/*selected current week dates when click the button*/
document.getElementById('week').addEventListener('click', function () {
    if (calendar.element.classList.contains('workweek')) {
         calendar.element.classList.remove('workweek')
    }
    calendar.element.classList.add('week');
});

function onChange(args: ChangedEventArgs) {
    let startOfWeek: any = moment(calendar.value).startOf('week');
    let endOfWeek: any = moment(calendar.value).endOf('week');
    if (calendar.element.classList.contains('workweek')) {
        getWeekArray(startOfWeek.day(1) , endOfWeek.day(5)) ;
    } else if (calendar.element.classList.contains("week")) {
        getWeekArray(startOfWeek, endOfWeek);
    }
}

function getWeekArray(startOfWeek: any, endOfWeek: any): void {
    let days: Date[] = [];
    let day: any = startOfWeek;
    while (day <= endOfWeek) {
        days.push(day.toDate());
        day = day.clone().add(1, 'd');
    }
    calendar.values = days;
}
```

{% endtab %}
