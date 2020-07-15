---
title: "How To"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the time picker"
---

# CSS customization

TimePicker allows you to customize the textbox and popup list appearance to suit your
application by using
[`cssClass`](../../api/timepicker#cssclass) property.

The below sample demonstrates customization of text appearance in a textbox, popup button, and popup list along with hover and active
state by using `e-custom-style` class. Following is the list of available classes used to customize the entire TimePicker component.

| **Class Name** | **Description** |
| --- | --- |
| e-time-wrapper | Applied to TimePicker wrapper element. |
| e-timepicker |  Applied to input element and TimePicker popup element. |
| e-time-wrapper.e-timepicker | Applied to input element only. |
| e-input-group-icon.e-time-icon | Applied to popup button. |
| e-float-text | Applied to floating label text element. |
| e-popup | Applied to popup element. |
| e-timepicker.e-popup | Applied to TimePicker popup element only. |
| e-list-parent | Applied to popup UL element. |
| e-timepicker.e-list-parent | Applied to TimePicker popup UL element only. |
| e-list-item | Applied to LI elements. |
| e-hover | Applied to LI element hovering time. |
| e-active | Applied to active LI element. |

{% tab template="timepicker/how-to", isDefaultActive = "true", sourceFiles="app.ts,index.html,style.css",
es5Template="timepicker-customcss-template" %}

```typescript
    import { TimePicker } from '@syncfusion/ej2-calendars';
    import { enableRipple } from '@syncfusion/ej2-base';

    //enable ripple style
    enableRipple(true);

    // creates timepicker
    let timeObject: TimePicker = new TimePicker({
        placeholder:'Select Time',
        // define the custom class
        cssClass: 'e-custom-style'
    });
    timeObject.appendTo('#element');

```

{% endtab %}
