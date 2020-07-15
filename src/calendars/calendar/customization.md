---
title: "Customization"
component: "Calendar"
description: "Calendar gives complete control to the user to customize overall appearance of the calendar in their application."
---

# Customization

Each day cell of the Calendar can be customized by using the
 [`renderDayCell`](../api/calendar/renderDayCellEventArgs#renderdaycelleventargs)
 event.

The following section demonstrates how to disable or highlight specific dates in a Calendar.

## Disable weekends

You can disable weekends of every month in a Calendar by using the
[`renderDayCell`](../api/calendar/renderDayCellEventArgs#renderdaycelleventargs)
event. The `renderDayCell` event offers the following arguments on each day cell creation to help you disable the dates.

| **View** | **Description** |
| --- | --- |
| `date` | Defines the current date of the Calendar. |
| `isDisabled` | Specifies whether the current date is to be disabled or not. |
| `isOutOfRange` | Defines whether the current date is out of range or not. |

The following example demonstrates how to disable weekends of every month.

{% tab template="calendar/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="calendar-disable-template" %}

```typescript

import { Calendar, RenderDayCellEventArgs } from '@syncfusion/ej2-calendars';
//Creates a calendar with weekends disabled.
let calendarObject: Calendar = new Calendar({
    renderDayCell: disabledDate,
    value: new Date()
});
calendarObject.appendTo('#element');

function disabledDate(args: RenderDayCellEventArgs): void {
    if (args.date.getDay() === 0 || args.date.getDay() === 6) {
        //Set 'true' to disable the weekends.
        args.isDisabled = true;
    }
}

```

{% endtab %}

## Day cell format

You can also highlight specific dates by adding custom CSS or element to the day cell by using the [`renderDayCell`](../api/calendar/renderDayCellEventArgs#renderdaycelleventargs) event.

You can customize the appearance of the Calendar by overriding the existing styles. The following list of CSS class names are used to customize the Calendar component.

| **Class Name** | **Description** |
| --- | --- |
| e-calendar | Applied to the Calendar. |
| e-header | Applied to the header.|
| e-title |Applied to the title. |
| e-icon-container | Applied to the previous and next icon container.|
| e-prev |  Applied  to the previous icon.|
| e-next | Applied to the next icon.|
| e-weekend | Applied to weekends.|
| e-other-month |  Applied to days of other months.|
| e-day | Applied to each day cell.|
| e-selected | Applied to the selected dates.|
| e-disabled | Applied to the disabled dates.|

The following example highlights the World Health Day (every 7th April) and World Forest Day (every 21st March) by using the
custom icon and ToolTip.

{% tab template="calendar/highlight-special", sourceFiles="app.ts,index.html,styles.css", es5Template="calendar-daycellformat-template" %}

```typescript

import { Calendar, RenderDayCellEventArgs } from '@syncfusion/ej2-calendars';

//Creates a Calendar with World Health Day and World Forest Day highlighted.
let calendarObject: Calendar = new Calendar({
    renderDayCell: customDates,
    value: new Date('03/10/2017')
});
calendarObject.appendTo('#element');

function customDates(args: RenderDayCellEventArgs): void {
    let span: HTMLElement;
    //Defines the custom HTML element to be added.
    span = document.createElement('span');
    //Uses "e-icons" class name to load Essential JS 2 built-in icons.
    span.setAttribute('class', 'e-icons highlight-day');
    if (+args.date.getDate() === 7 && +args.date.getMonth() == 3) {
        //Appends the span element to day cell.
        args.element.appendChild(span);
        //Sets the custom tooltip to the special dates.
        args.element.setAttribute('title', 'World health day!');
        //Uses "special" class name to highlight special dates that you can refer in "styles.css".
        args.element.className = 'special';
    }
    if (+args.date.getDate() === 21 && +args.date.getMonth() == 2) {
        args.element.appendChild(span);
        args.element.className = 'special';
        //Sets the custom tooltip to the special dates.
        args.element.setAttribute('title', 'World forest day');
    }
}

```

{% endtab %}

## Highlight weekends

You can highlight the weekends of every month in a Calendar by using the
[`renderDayCell`](../api/calendar/renderDayCellEventArgs#renderdaycelleventargs)
event. The following example demonstrates how to highlights the weekends of every month.

{% tab template="calendar/highlight-weekend", sourceFiles="app.ts,index.html,styles.css", es5Template="calendar-highlight-template" %}

```typescript

import { Calendar, RenderDayCellEventArgs } from '@syncfusion/ej2-calendars';
//Creates a calendar with weekends highlighted.
let calendarObject: Calendar = new Calendar({
    renderDayCell: highlightDate,
    value: new Date()
});
calendarObject.appendTo('#element');

function highlightDate(args: RenderDayCellEventArgs): void {
    if (args.date.getDay() === 0 || args.date.getDay() === 6) {
        // To highlight the week end of every month
       args.element.classList.add('e-highlightweekend');
    }
}

```

{% endtab %}

## See Also

* [Add the external button in the Calendar popup](./how-to/set-clear-button-in-calendar)
* [How to skip a month in Calendar](./how-to/skip-a-month-in-calendar)
* [How to change the first day of week](./how-to/change-the-first-day-of-week)
* [How to customize the calendar day header](./how-to/customize-the-calendar-day-header)
