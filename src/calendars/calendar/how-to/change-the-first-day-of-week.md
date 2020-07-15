---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Change the first day of the week

The Calendar provides an option to change the first day of the week by using the [`firstDayOfWeek`](../../api/calendar#firstdayofweek)
property. Generally, the day of the week starts from 0 (Sunday) and ends with 6 (Saturday).

> By default, the first day of the week is culture specific.

The following example shows the Calendar with `Tuesday` as the first day of the week.

{% tab template="calendar/getting-started", sourceFiles="app.ts,index.html,styles.css"
,es5Template="calendar-firstdayofweek-template" %}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
//creates  a calendar with Tuesday as the first day of the week.
let calendarObject: Calendar = new Calendar({
    //sets the first day of the week.
    firstDayOfWeek: 2
});
calendarObject.appendTo('#element');
```

{% endtab %}
