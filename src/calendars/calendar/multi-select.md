---
title: "Multi Selection"
component: Calendar
description: "Calendar supports multiple date selection to allow users to select more than one date."
---
# Multi Selection

Calendar provides an option to select **single** or **multiple dates** by using `isMultiSelection` and `values` properties. By default, `isMultiSelection` property will be in disabled state.

| API | Type | Description |
|------|------|----------------------|
| `isMultiSelection`| **Boolean**| Enables the multi-selection option in the Calendar control |
|`values`| **Date[]** | Gets or sets the date range values in multi-selection option |

The following example demonstrates the functionality of  `isMultiSelection` property and `values` properties in the Calendar control.

{% tab template="calendar/getting-started", sourceFiles="app.ts,index.html,styles.css",es5Template="calendar-multiselect-template" %}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';

/*Initialize the calender component*/
let calendar: Calendar = new Calendar({
    isMultiSelection: true,
    values: [new Date('1/1/2020'), new Date('1/15/2020'), new Date('1/3/2020'), new Date('1/25/2020')]
});
calendar.appendTo('#element');

```

{% endtab %}

## See Also

* [Select a sequence of dates in Calendar](./how-to/select-a-sequence-of-dates-in-calendar)
