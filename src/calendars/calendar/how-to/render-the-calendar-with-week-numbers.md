---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Render the Calendar with week numbers

You can enable `weekNumbers` in the Calendar by using the [`weekNumber`](../../api/calendar#weeknumber) property.

{% tab template="calendar/getting-started" , sourceFiles="app.ts,index.html,styles.css"
,es5Template="calendar-weeknumber-template" %}

```typescript

import { Calendar } from '@syncfusion/ej2-calendars';
//creates a calendar with weekNumber enabled
let calendarObject: Calendar = new Calendar({
    //sets the weekNumber
    weekNumber: true
});
calendarObject.appendTo('#element');

```

{% endtab %}