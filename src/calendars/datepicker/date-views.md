---
title: "Date Views"
component: "DatePicker"
description: "Pre-defined views in date picker allows to perform easy navigation to select any date."
---

# Start and Depth View

The DatePicker has the following predefined views
that provides a flexible way to navigate back and forth to select the date.

| **View** | **Description** |
| --- | --- |
| month (default) | Displays the days in a month |
| year | Displays the months in a year |
| decade | Displays the years in a decade |

## Start view

You can use the [`start`](../api/datepicker#start) property to define the initial rendering view.

The following example demonstrates how to create a DatePicker with `decade` as initial rendering view.

{% tab template="datepicker/getting-started", isDefaultActive = "true",sourceFiles="app.ts,index.html"
,es5Template="datepicker-startview-template"  %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
 //creates a datepicker with year view.
let datepickerObj: DatePicker = new DatePicker({
    // sets the placeholder
    placeholder:'Enter date',
    //sets the start
    start:'Decade'
});
datepickerObj.appendTo('#element');
```

{% endtab %}

## Depth view

Define the [`depth`](../api/datepicker#depth) property to control the view navigation.

> Always the depth view has to be smaller than the start view, otherwise the view restriction
will be not restricted.

The following example demonstrates how to create a DatePicker that allows users to select a month.

{% tab template="datepicker/getting-started", isDefaultActive = "true",sourceFiles="app.ts,index.html"
,es5Template="datepicker-depthview-template"  %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
//creates a datepicker with decade view and navigate up to year view.
let datepickerObj: DatePicker = new DatePicker({
    //sets the start
    start:'Decade',
    //sets the depth
    depth:'Year',
    // sets the placeholder
    placeholder:'Enter date',
});
datepickerObj.appendTo('#element');
```

{% endtab %}

> To know more about Calendar views refer the Calendar's
[Calendar Views](../calendar/calendar-views/)
section.