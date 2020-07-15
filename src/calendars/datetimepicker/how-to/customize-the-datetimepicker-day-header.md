---
title: "How To"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the datetimepicker"
---

# Customize the datetimepicker day header

You can change the format of the day that to be displayed in header using [`dayHeaderFormat`](../../api/datetimepicker#dayheaderformat) property. By default, the format is `Short`.

You can find the possible formats on below.

| **Name** | **Description** |
|------|---------------------|
| `Short` | Sets the short format of day name (like Su ) in day header. |
| `Narrow` | Sets the single character of day name (like S ) in day header. |
| `Abbreviated` | Sets the min format of day name (like Sun ) in day header. |
| `Wide` | Sets the long format of day name (like Sunday ) in day header. |

{% tab template="datetimepicker/header-format" , sourceFiles="app.ts,index.html",
es5Template="datetimepicker-header-format-template" %}

```typescript

import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

// creates datetimepicker component
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    dayHeaderFormat: "Short"
});
datetimepickerObject.appendTo('#element');

let formatLabel: DropDownList = new DropDownList({
        // set the height of the popup element
        popupHeight: '200px',
        // bind the change event
            change: (args: any) => {
                 datetimepickerObject.dayHeaderFormat = args.value;
            }
 });
 formatLabel.appendTo('#select');
```

{% endtab %}
