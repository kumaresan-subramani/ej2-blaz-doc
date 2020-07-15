---
title: "Accessibility"
component: "DateRangePicker"
description: "Date range picker component support accessibility that helps to access all the features through the keyboard, on-screen readers, or other assertive technology devices."
---

# Accessibility

The web accessibility makes web content and web applications more accessible for people with disabilities. It especially helps in dynamic content change and development of advanced user interface controls with AJAX, HTML, JavaScript, and related technologies.
DateRangePicker provides built-in compliance with [WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices) specifications. WAI-ARIA
support is achieved through the attributes
like `aria-expanded`, `aria-disabled`, and `aria-activedescendant`
applied as an input element.

To know about the accessibility of Calendar, refer to the Calendar's
[Accessibility](../calendar/accessibility/) section.

It helps people with disabilities by providing information about the widget for assistive technology in the screen readers. DateRangePicker component contains grid role and grid cell for each day cell.

* **Aria-expanded**: Indicates the currently selected date of the DateRangePicker component.

* **Aria-disabled**:  Indicates the disabled state of the DateRangePicker component.

## Keyboard Interaction

Use the below keys to interact with the DateRangePicker.
This component implements the keyboard navigation support by following the  [WAI-ARIA practices](http://www.w3.org/WAI/PF/aria-practices).

It supports the following list of shortcut keys:

Input Navigation

Before opening the popup, use the following list of keys to
control the popup element.

| **Press** | **To do this** |
| --- | --- |
| <kbd>Alt +  Down Arrow</kbd> | Opens the popup. |
| <kbd>Alt +  Up Arrow</kbd> | Closes the popup.|
| <kbd>Esc</kbd> | Closes the popup. |

Calendar Navigation

Use the following list of keys to navigate the currently focused Calendar after the popup has opened.

| **Press** | **To do this** |
| --- | --- |
| <kbd>Upper Arrow</kbd>  | Focuses the same day of the previous week. |
| <kbd>Down Arrow</kbd>  | Focuses the same day of the next week. |
| <kbd>Left Arrow</kbd>  | Focuses the day before. |
| <kbd>Right Arrow</kbd>  | Focuses the next day. |
| <kbd>Home</kbd>  | Focuses the first day of the month. |
| <kbd>End</kbd>  | Focuses the last day of the month. |
| <kbd>Page Up</kbd>  | Focuses the same date of the previous month. |
| <kbd>Page Down</kbd>  | Focuses the same date of the next month. |
| <kbd>Enter</kbd>  | Selects the currently focused date. |
| <kbd>Shift + Page Up</kbd>  | Focuses the same date for the previous year. |
| <kbd>Shift + Page Down</kbd>  | Focuses the same date for the next year. |
| <kbd>Control + Home</kbd>  | Focuses the first date of the current year. |
| <kbd>Control + End</kbd>  | Focuses the last date of the current year. |
| <kbd>Alt + Right</kbd>  | Focuses through out the pop-up container in forward direction. |
| <kbd>Alt + Left</kbd>  | Focuses through out the pop-up container in backward direction. |

> To focus the DateRangePicker component, use the `alt+t` keys.

{% tab template="daterangepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",es5Template="daterangepicker-accessibility-template"%}

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates a  DateRangePicker component
let daterangeObject: DateRangePicker = new DateRangePicker({
    // sets the placeholder
    placeholder: 'Select a range'
    });
daterangeObject.appendTo('#element');

document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84 /* t */) {
        // press alt+t to focus the component.
        daterangeObject.element.focus();
    }
};

```

{% endtab %}