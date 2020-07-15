---
title: "Customization"
component: "DateRangePicker"
description: "Date range picker gives complete control to the user to customize overall appearance of the date range picker in their application."
---

# Customization

The DateRangePicker is available for UI customization that can be achieved by using available properties and events in the component.

## Day cell format

The DateRangePicker is available for UI customization based on your application requirements. It can be achieved by using [`renderDayCell`](../api/daterangepicker/renderDayCellEventArgs#renderdaycelleventargs)
 event that provides an option to customize each day cell on rendering.

The following example disables the weekends of every month by using `renderDayCell` event.

{% tab template="daterangepicker/getting-started", sourceFiles="app.ts,index.html"
,es5Template="daterangepicker-daycellformat-template" %}

```typescript
import { DateRangePicker, RenderDayCellEventArgs } from '@syncfusion/ej2-calendars';
// creates daterangepicker with placeholder.
let daterangeObject: DateRangePicker = new DateRangePicker({
    // Bind the renderDayCell event to customize the each day cell.
    renderDayCell: onRenderCell,
    // sets the placeholder
    placeholder: 'Select a range'
});
daterangeObject.appendTo('#element');

function onRenderCell(args: RenderDayCellEventArgs): void {
    if (args.date.getDay() == 0 || args.date.getDay() == 6) {
        //sets isDisabled to true to disable the date.
        args.isDisabled = true;
    }

}
```

{% endtab %}

## Preset Ranges

DateRangePicker provides an option to set the predefined ranges via [`presets`](../api/daterangepicker/#presets) property with the corresponding label. This property will
accept the values in the order of label, start date (date object), end date (date object), and append these
ranges to the presets pop-up for quick selection. In the following sample, you can easily choose the
frequently used range options from the list of ranges.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html" ,es5Template="daterangepicker-presets-template"%}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
let today: Date = new Date();
let currentYear: number = today.getFullYear();
let currentMonth: number = today.getMonth();
let currentDay: number = today.getDate();
// creates a daterangepicker with predefined ranges (label, start date, end date)
let daterangeObject: DateRangePicker = new DateRangePicker({
    placeholder: 'Select a range',
        presets: [
            { label: 'Today', start: new Date(), end: new Date() },
            { label: 'This Month', start: new Date(new Date().setDate(1)), end: new Date() },
            { label: 'Last Month', start: new Date(new Date(new Date().setMonth(new Date().getMonth() - 1)).setDate(1)), end: new Date() },
            { label: 'Last Year', start: new Date(new Date().getFullYear() - 1, 0, 1), end: new Date() },

        ]

});
daterangeObject.appendTo('#element');

```

{% endtab %}

## First day of week

Start day in a week will differ based on the culture, but you can also customize this based on the application needs.
For this, you have to make use of [`firstDayOfWeek`](../api/daterangepicker#firstdayofweek) property.
By default, first day of a week in en-US is Sunday. In the following example it is customized to Monday with the help of this property.

{% tab template="daterangepicker/getting-started" , sourceFiles="app.ts,index.html",
es5Template="daterangepicker-firstdayofweek-template" %}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates daterangepicker with readonly.
let daterangeObject: DateRangePicker = new DateRangePicker({
    // sets the firstDayOfWeek to Monday.
    firstDayOfWeek:1, placeholder:"Select Range"

});
daterangeObject.appendTo('#element');

```

{% endtab %}

## See Also

* [How to customize DateRangePicker using cssClass](./how-to/customization-using-cssclass)
* [How to disable DateRangePicker control](./how-to/disable-the-daterangepicker-component)
* [How to customize the DateRangePicker day header](./how-to/customize-the-daterangepicker-day-header)