---
title: "Accessibility"
component: "Calendar"
description: "The calendar component support accessibility that helps to access all the features through the keyboard, on-screen readers, or other assertive technology devices."
---

# Accessibility

The web accessibility makes web content and web applications more accessible for disabled people. It especially helps in dynamic content change and development of advanced user interface controls  with AJAX, HTML, JavaScript, and related technologies.

Calendar provides built-in compliance with
[WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices) specifications. WAI-ARIA support is achieved through attributes like `aria-label`, `aria-selected`, `aria-disabled`, and `aria-activedescendant`
applied for navigation buttons, disable and active day cells.

It helps disabled persons by providing the information about the widget for assistive technology in the screen readers. Calendar component contains grid role and grid cell for each day cell.

* **Aria-label**: This attribute provides text labels for an object for the previous and next month's elements. It helps the screen reader object to read.

* **Aria-selected**: Indicates the currently selected date of the Calendar component.

* **Aria-disabled**: Indicates the disabled state of the Calendar component.

* **Aria-activedescendent**: Helps in managing the current active child of the Calendar component.

* **Role**: Gives information to assistive technologies about how to handle each element in a widget.

* **Grid-cell**: Defines the individual cell that can be focused and selected.

## Keyboard interaction

You can use the following keys to interact with the Calendar. This component implements keyboard navigation support by following the [WAI-ARIA practices](http://www.w3.org/WAI/PF/aria-practices).

It supports the following list of shortcut keys:

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
| <kbd>Control + Upper Arrow</kbd>  | Moves to the inner level of view like month to year and year to decade. |
| <kbd>Control + Down Arrow</kbd>  | Moves out from the depth level view like decade to year and year to month. |
| <kbd>Control + Home</kbd>  | Focuses the first date of the current year. |
| <kbd>Control + End</kbd>  | Focuses the last date of the current year. |

> To focus the Calendar component, use `alt+t` keys.

{% tab template="calendar/getting-started", isDefaultActive = "true",
sourceFiles="app.ts,index.html styles.css", es5Template="calendar-accessibility-template"%}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
// creates a Calendar component.
let calendarObj: Calendar = new Calendar();
calendarObj.appendTo('#element');

document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84) {
        // press alt+t to focus the control.
        (<HTMLElement>calendarObj.element.querySelectorAll('.e-content table')[0]).focus();
    }
};
```

{% endtab %}