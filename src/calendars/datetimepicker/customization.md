---
title: "Customization"
component: "DateTimePicker"
description: "Date time picker gives complete control to the user to customize overall appearance of the date time picker in their application."
---

# Customization

The DateTimePicker is available for UI customization that can be achieved by using available properties and events in the component.

## Day and Time Cell format

The DateTimePicker is available for UI customization based on your application requirements.
It can be achieved by using [`renderDayCell`](../api/datetimepicker/renderDayCellEventArgs#renderdaycelleventargs)
 event that provides an option to customize each day cell on rendering.

The following example disables the weekends of every month by using `renderDayCell` event.

{% tab template="datetimepicker/getting-started", sourceFiles="app.ts,index.html"
,es5Template="datetimepicker-daytimecellformat-template" %}

```typescript
import { DateTimePicker, RenderDayCellEventArgs, ItemEventArgs } from '@syncfusion/ej2-calendars';
// creates datetimepicker with placeholder.
let datetimeObject: DateTimePicker = new DateTimePicker({
    // Bind the renderDayCell event to customize the each day cell.
    renderDayCell: onRenderCell,
    // sets the placeholder
    placeholder: 'Select a date and time'
});
datetimeObject.appendTo('#element');

function onRenderCell(args: RenderDayCellEventArgs): void {
    if (args.date.getDay() == 0 || args.date.getDay() == 6) {
         //sets isDisabled to true to disable the date.
        args.isDisabled = true;
    }

}
```

{% endtab %}

## See Also

* [How to disable the DateTimePicker control](./how-to/disable-the-datetimepicker-component)
* [How to customize the DateTimePicker day header](./how-to/customize-the-datetimepicker-day-header)