---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Show dates of other months

The following example demonstrates how to show dates of other months.

Using the styles below, you can bring the dates of other months to visibility from its hidden state.

```css
.e-calendar .e-content tr.e-month-hide,
.e-calendar .e-content td.e-other-month>span.e-day {
    display: block;
}

.e-calendar .e-content td.e-month-hide,
.e-calendar .e-content td.e-other-month {
    pointer-events: auto;
    touch-action: auto;
}
```

{% tab template="calendar/how-to-othermonth", sourceFiles="app.ts,index.html,styles.css"
,es5Template="calendar-othermonth-template" %}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
//creates a calendar with dates of other months shown.
let calendarObject: Calendar = new Calendar({
});
calendarObject.appendTo('#element');
```

{% endtab %}
