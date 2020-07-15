---
title: "Strict Mode"
component: "TimePicker"
description: "The strictMode option allows the user to enter only the valid time value within the specified min/max time range in textbox."
---

# Strict mode

The [`strictMode`](../api/timepicker#strictmode)
is an act that allows you to enter only valid time value within the specified min/max
range in the textbox. If the time value is invalid, the component value sets to the previous value.
If the time value is
out of range, the component sets the time value to min/max value.

The following example demonstrates the TimePicker in `strictMode` with min/max range of `10:00 AM` to
`4:00 PM` . It allows you to enter
only valid time within the specified range. If you enter the out-of-range value like
`8:00 PM`,
the value sets to the max time `4:00 PM` as the value `8:00 PM` is greater than `max` value
of `4:00 PM`. If you enter invalid time value like `9:00 tt`, the value sets to the previous value.

{% tab template="timepicker/getting-started",sourceFiles="app.ts,index.html",
es5Template="timepicker-strictmodeenabled-template" %}

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);


let timeObject: TimePicker = new TimePicker({
    strictMode: true,
    min: new Date('7/18/2017 10:00 AM'),
    max: new Date('7/18/2017 4:00 PM'),
    value: new Date('7/18/2017 8:00 PM'),

});
timeObject.appendTo('#element');

```

{% endtab %}

By default, the TimePicker act in strictMode `false` state, that allows to enter the invalid or out-of-range time in textbox.

If the time is out-of-range or invalid, then the model value will be set to `out of range` time
value or `null` respectively with highlighted `error` class to indicates the time is out of range or invalid.

The following example demonstrates the `strictMode` as `false`. Here, it allows to enter the
valid or invalid value in textbox.
If you are entering the out-of-range or invalid time value, then the model value will be set to
`out of range` time value or `null` respectively with highlighted `error` class to indicates the time is out of range or invalid.

{% tab template="timepicker/getting-started" , sourceFiles="app.ts,index.html",
es5Template="timepicker-strictmodedisabled-template" %}

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);


let timeObject: TimePicker = new TimePicker({
    strictMode: false,
    min: new Date('7/18/2017 10:00 AM'),
    max: new Date('7/18/2017 4:00 PM'),
    value: new Date('7/18/2017 8:00 PM'),

});
timeObject.appendTo('#element');

```

{% endtab %}

> If the value of `min` or `max` property is changed through code behind, update the `value` property to set within the range.