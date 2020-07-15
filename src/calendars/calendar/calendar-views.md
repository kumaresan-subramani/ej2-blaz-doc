---
title: "Calendar Views"
component: "Calendar"
description: "Pre-defined views in calendar allows to perform easy navigation to select any date."
---

# Calendar Views

The Calendar has the following predefined views
that provide a flexible way to navigate back and forth when selecting dates.

| **View** | **Description** |
| --- | --- |
| month (default) | Displays the days in a month. |
| year | Displays the months in a year. |
| decade | Displays the years in a decade. |

When view is defined to the [`start`](../api/calendar#start)
property of the Calendar, it allows you to set the initial view on rendering.

The following example demonstrates how to set the `year` as the start view of the Calendar.

{% tab template="calendar/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css" , es5Template="calendar-view-template"%}

```typescript
import { Calendar, ChangedEventArgs } from '@syncfusion/ej2-calendars';
//creates a calendar with year view.
let calendarObject: Calendar = new Calendar({
    //sets the start view.
    start: "Year",
    //sets the value.
    value: new Date()
});
calendarObject.appendTo('#element');
```

{% endtab %}

## View restriction

Calendar view navigation can be restricted by defining the  [`start`](../api/calendar#start)
 and [`depth`](../api/calendar#depth)
property that allows you to select the date from that view.

By defining the start and depth property with the different view, drill-
down and drill-up views navigation can be limited to the user. Calendar views will be drill-down up to the
view which is set in `depth` property and drill-up up to the view which is set in `start` property.

The following example displays the Calendar in `decade` view, and allows you to select a date in `month` view.

> Depth view should always be smaller than the start view. If the views are the same, then the Calendar view remains unchanged.

{% tab template="calendar/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="calendar-viewrestriction-template" %}

```typescript
import { Calendar, ChangedEventArgs } from '@syncfusion/ej2-calendars';
//creates a calendar with decade view and navigates up to year view.
let calendarObject: Calendar = new Calendar({
    //sets the start view.
    start: "Decade",
    //sets the depth view.
    depth: "Year"
});
calendarObject.appendTo('#element');
```

{% endtab %}