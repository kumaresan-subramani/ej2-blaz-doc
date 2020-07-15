---
title: "Time Range"
component: "TimePicker"
description: "Time picker has `min` and `max` properties which restricts the user from selecting a value out of given time range"
---

# Time Range

TimePicker provides an option to select a time value within a specified range by using the
[`min`](../api/timepicker#min)
and
[`max`](../api/timepicker#max)
properties.  The min value should always be lesser than the max value.

When the min and max properties are configured and the selected time value is out-of-range or
invalid, then the model value will be set to `out of range` time value or `null` respectively
with highlighted `error` class to indicates the time is out of range or invalid.

The value property depends on the min/max with respect to [`strictMode`](./strict-mode) property.

The following example allows you to select a time value within a range of `9:00 AM` to `11:30 AM`.

{% tab template="timepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css",es5Template="timepicker-range-template" %}

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);

//creates a timepicker with min and max property
let timeObject: TimePicker = new TimePicker({
    //sets the min value
    min: new Date('3/8/2017 9:00 AM'),
    //sets the max value
    max: new Date('3/8/2017 11:30 AM'),
    //sets the value
    value: new Date('3/8/2017 11:00 AM')
});
timeObject.appendTo('#element');

```

{% endtab %}

> If the value of `min` or `max` property is changed through code behind you have to update the `value` property to set within the range.

## Time Range customization using two TimePicker components

Here, two TimePicker components are used to select the start and end time. The below sample illustrates the appointment time selection scenario with the start and end time option.

Before the start time selection, the end time TimePicker is in disable state. When the start time is selected, then you will be able to select the end time or else, need to select the entire business hours 9:00 to 18:00 from the Business Hours option. Once the options are checked, both the TimePicker components goes to readonly state.

{% tab template="timepicker/time-range-customization", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css",es5Template="timepicker-range-customization-template" %}

```typescript

import { TimePicker, ChangeEventArgs  } from '@syncfusion/ej2-calendars';
import { CheckBox, ChangeEventArgs as checkboxChange } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);
 let value: Date;
    let isStartTimeChange: Boolean = true;
    let startTime: TimePicker = new TimePicker({
        change: onEnableEndTime
    });
    startTime.appendTo('#start');
    let endTime: TimePicker = new TimePicker({
        enabled: false
    });
    endTime.appendTo('#end');

    let checkboxObject: CheckBox = new CheckBox({ label: 'Business Hours', change: changeTime });
    checkboxObject.appendTo('#dayRange');

    let endInput: HTMLInputElement = <HTMLInputElement>document.getElementById('end');
    function changeTime(args: checkboxChange): void {
        /*To determine whether we have selected business hours or not*/
        isStartTimeChange = false;
        if (args.checked) {
            /*Business hours*/
            startTime.value = new Date('9/6/2017 9:00');
            endTime.enabled = true;
            endTime.value = new Date('9/6/2017 18:00');
            startTime.readonly = true;
            endTime.readonly = true;
        } else {
            endTime.value = null;
            startTime.value = null;
            endInput.value = '';
            startTime.readonly = false;
            endTime.readonly = false;
            endTime.enabled = false;
        }
    }
    function onEnableEndTime(args: ChangeEventArgs): void {
        /*Enables end time if start time is selected*/
        if (isStartTimeChange) {
            endTime.enabled = true;
            endTime.value = null;
            endInput.value = '';
            value = new Date(+args.value);
            value.setMinutes(value.getMinutes() + endTime.step);
            endTime.min = value;
        } else {
            isStartTimeChange = true;
        }
    }

```

{% endtab %}