---
title: "Islamic Calendar"
component: "Calendar"
description: "Calendar supports to display the Islamic Calendar (Hijri Calendar)."
---

# Islamic-Calendar

In addition to the Gregorian calendar, the calendar control supports displaying the Islamic calendar (Hijri calendar). **Islamic calendar** or **Hijri calendar** is a `lunar calendar` consisting of 12 months in a year of 354 or 355 days. To know more about Islamic calendar, please refer this [wikipedia](https://en.wikipedia.org/wiki/Islamic_calendar).

Also, it consists of all Gregorian calendar functionalities as like min and max date, week number, start day of the week, multi selection, enable RTL, start and depth view, localization, highlight and customize the specific dates.

By default, calendar mode is in **Gregorian**. You can enable the Islamic mode by setting the **calendarMode** as **Islamic**. Also, need to import and injecting the `Islamic` module from `ej2-calendars` as shown below.

> import { Islamic, Calendar } from '@syncfusion/ej2-calendars';\
> Calendar.Inject(Islamic);

The following example demonstrates how to display the Islamic Calendar (Hijri Calendar).

{% tab template="calendar/islamic-calendar", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css" , es5Template="calendar-islamic-template"%}

```typescript
import { Calendar, Islamic, RenderDayCellEventArgs } from '@syncfusion/ej2-calendars';
import { addClass } from '@syncfusion/ej2-base';
// 'Islamic' module injection
Calendar.Inject(Islamic);

//creates a calendar with islamic mode.
let calendarObject: Calendar = new Calendar({
    // To display the Islamic calendar
    calendarMode: 'Islamic',
    renderDayCell: customDates
});
calendarObject.appendTo('#element');

function customDates(args: RenderDayCellEventArgs): void {
  /*Date need to be disabled*/
  if ( args.date.getDate() === 12 || args.date.getDate() === 17 || args.date.getDate() === 28) {
    args.isDisabled = true;
  }
  /*Dates need to be customized*/
  if (args.date.getDate() === 13) {
    let span: HTMLElement;
    span = document.createElement('span');
    args.element.children[0].className += 'e-day sf-icon-cup highlight';
    addClass([args.element], ['special', 'e-day', 'dinner']);
    args.element.setAttribute('data-val', ' Dinner !');
    args.element.appendChild(span);
  }
  if (args.date.getDate() === 23) {
    let span: HTMLElement;
    span = document.createElement('span');
    args.element.children[0].className += 'e-day sf-icon-start highlight';
    span.setAttribute('class', 'sx !');
    //use the imported method to add the multiple classes to the given element
    addClass([args.element], ['special', 'e-day', 'holiday']);
    args.element.setAttribute('data-val', ' Holiday !');
    args.element.appendChild(span);
  }
}
```

{% endtab %}