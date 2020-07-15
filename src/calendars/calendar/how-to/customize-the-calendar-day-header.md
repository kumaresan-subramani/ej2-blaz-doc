---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Customize the calendar day header

You can change the format of the day that to be displayed in header using [`dayHeaderFormat`](../../api/calendar#dayheaderformat) property. By default, the format is `Short`.

You can find the possible formats on below.

| **Name** | **Description** |
|------|---------------------|
| `Short` | Sets the short format of day name (like Su ) in day header. |
| `Narrow` | Sets the single character of day name (like S ) in day header. |
| `Abbreviated` | Sets the min format of day name (like Sun ) in day header. |
| `Wide` | Sets the long format of day name (like Sunday ) in day header. |

{% tab template="calendar/header-format" , sourceFiles="app.ts,index.html,styles.css"
,es5Template="calendar-headerformat-template" %}

```typescript

import { Calendar } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

let calendarObject: Calendar = new Calendar({
    dayHeaderFormat: "Short"
});
calendarObject.appendTo('#element');

let formatLabel: DropDownList = new DropDownList({
        // set the height of the popup element
        popupHeight: '200px',
        // bind the change event
            change: (args: any) => {
                 calendarObject.dayHeaderFormat = args.value;
            }
 });
 formatLabel.appendTo('#select');
```

{% endtab %}