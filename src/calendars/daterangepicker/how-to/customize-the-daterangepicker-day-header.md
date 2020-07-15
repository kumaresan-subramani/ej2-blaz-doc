---
title: "How To"
component: "DateRangePicker"
description: "Miscellaneous aspects of customizing the date range picker"
---

# Customize the daterangepicker day header

You can change the format of the day that to be displayed in header using [`dayHeaderFormat`](../../api/daterangepicker#dayheaderformat) property. By default, the format is `Short`.

You can find the possible formats on below.

| **Name** | **Description** |
|------|---------------------|
| `Short` | Sets the short format of day name (like Su ) in day header. |
| `Narrow` | Sets the single character of day name (like S ) in day header. |
| `Abbreviated` | Sets the min format of day name (like Sun ) in day header. |
| `Wide` | Sets the long format of day name (like Sunday ) in day header. |

{% tab template="daterangepicker/header-format" , sourceFiles="app.ts,index.html",
es5Template="daterangepicker-header-format-template" %}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

// creates daterangepicker component
let daterangepickerObject: DateRangePicker = new DateRangePicker({
    dayHeaderFormat: "Short",
    cssClass: "format-wide"
});
daterangepickerObject.appendTo('#element');

let formatLabel: DropDownList = new DropDownList({
        // set the height of the popup element
        popupHeight: '200px',
        // bind the change event
            change: (args: any) => {
                 daterangepickerObject.dayHeaderFormat = args.value;
            }
 });
 formatLabel.appendTo('#select');
```

{% endtab %}
