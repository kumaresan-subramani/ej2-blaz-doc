---
title: "Strict Mode"
component: "DatePicker"
description: "The strictMode option allows the user to enter only the valid date value within the specified min/max range in textbox."
---

# Strict Mode

The [`strictMode`](../api/datepicker#strictmode)
is an act, that allows the user to enter only the valid date within the specified min/max
range in textbox. If the date is invalid, then the component will stay with the previous value.
Else, if the date is
out of range, then the component will set the date to the min/max date.

The following example demonstrates the DatePicker in `strictMode` with min/max range of 5th to
25th in a month of May. Here, it allows to enter
only the valid date within the specified range. If you are trying to enter the out-of-range value as
like 28th of May,
then the value will set to the max date of 25th May. Since the value 28th is greater than to `max` value
of 25th. Or else if you are trying
to enter the invalid date, then the value will stay with the previous value.

{% tab template="datepicker/getting-started" ,sourceFiles="app.ts,index.html",
es5Template="datepicker-strictdisabled-template"  %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
// creates a datepicker with strictMode property
let datepickerObject: DatePicker = new DatePicker({
    // sets the strictMode
    strictMode: true,
    // sets the format
    format: 'dd/MM/yyyy',
    // sets the value
    value: new Date('5/28/2017'),
    //sets the min
    min: new Date('5/5/2017'),
    //sets the max
    max: new Date('5/25/2017')
});
datepickerObject.appendTo('#element');
```

{% endtab %}

By default, the DatePicker act in strictMode `false` state, that allows to enter the invalid or out-of-range date in textbox.

If the date is out-of-range or invalid, then the model value will be set to `out of range` date
value or `null` respectively with highlighted  `error` class to indicates the date is out of range or invalid.

The following example demonstrates the `strictMode` as `false`. Here, it allows to enter the
valid or invalid value in textbox.
If you are entering out-of-range or invalid date value, then the model value will be set to
`out of range` date value or `null` respectively with highlighted  `error` class to indicates
the date is out of range or invalid.

{% tab template="datepicker/getting-started", sourceFiles="app.ts,index.html",es5Template="datepicker-strictdisabled-template" %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
// creates a datepicker with strictMode property
let datepickerObject: DatePicker = new DatePicker({
    // sets the value
    value: new Date('5/28/2017'),
    //sets the min
    min: new Date('5/5/2017'),
    //sets the max
    max: new Date('5/25/2017'),
    // sets the format
    format: 'dd/MM/yyyy',
    // sets the placeholder
    placeholder: 'Enter date'
});
datepickerObject.appendTo('#element');
```

{% endtab %}

> If the value of `min` or `max` properties changed through code behind,
then you have to update the `value` property to set within the range.
