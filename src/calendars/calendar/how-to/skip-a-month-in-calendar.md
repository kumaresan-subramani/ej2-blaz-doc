---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Skip a month in the Calendar

The following example demonstrates how to skip a month in the Calendar while clicking the previous and next icons. In the example below,  the [`navigated`](../../api/calendar#navigated) event is used to skip a month with [`navigateTo`](../../api/calendar#navigateto)
method.

{% tab template="calendar/getting-started", sourceFiles="app.ts,index.html,styles.css"
,es5Template="calendar-skipmonth-template" %}

```typescript
import { Calendar, NavigatedEventArgs } from '@syncfusion/ej2-calendars';
//Creates a calendar component.
let calendarObject: Calendar = new Calendar({ navigated: onNavigate });
calendarObject.appendTo('#element');
//Skips a month while cliking previous and next icons in month view.
function onNavigate(args: NavigatedEventArgs) {
    let date: Date;
    if ((<HTMLElement>args.event.currentTarget).classList.contains('e-next')) {
        //Increments the month while clicking the next icon.
        date = new Date(args.date.setMonth(args.date.getMonth() + 1));
    }
    if ((<HTMLElement>args.event.currentTarget).classList.contains('e-prev')) {
        //Decrements the month while clicking the previous icon.
        date = new Date(args.date.setMonth(args.date.getMonth() - 1));
    }
    if (args.view == 'month') {+
        calendarObject.navigateTo('month', date);
    }
}
```

{% endtab %}
