---
title: "Accessibility"
component: "DateTimePicker"
description: "Date time picker component support accessibility that helps to access all the features through the keyboard, on-screen readers, or other assertive technology devices."
---

# Accessibility

The Web accessibility defines a way to make web content and web applications
more accessible to disabled people. It especially helps the dynamic content change
and advanced user interface controls developed with Ajax, HTML, JavaScript, and related technologies.

DateTimePicker provides built-in compliance with the
[WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices) specifications. WAI-ARIA
supports is achieved through the attributes
like `aria-expanded`, `aria-disabled`, `aria-activedescendant`
applied to the input element.

To know about the accessibility of Calendar refer to the Calendar's
[Accessibility](../calendar/accessibility/)
section.

It helps to provide information about the widget
for assistive technology to the disabled person in
screen reader.

* **Aria-expanded**: attributes indicates the state of a collapsible element.

* **Aria-disabled**: attribute indicates the disabled state of this DateTimePicker component.

* **Aria-activedescendent**: attribute helps in managing the current active child of the DateTimePicker component.

## Keyboard Interaction

You can use the following keys to interact with the DateTimePicker.
The component implements the keyboard navigation support by following the  [WAI-ARIA practices](http://www.w3.org/WAI/PF/aria-practices).

DateTimePicker supports the below list of shortcut keys.

Input Navigation

Before opening the popup, use the below list of keys to `DateTimePicker`
control the popup element.

| **Press** | **To do this** |
| --- | --- |
| <kbd>Alt +  Down Arrow</kbd> | Open the select popup |
| <kbd>Alt +  Down Arrow + Alt +  Down Arrow </kbd> | Toggle between two popups |

Calendar Navigation

Use the below list of keys to interact with the Calendar after the DatePicker popup has opened.

| **Press** | **To do this** |
| --- | --- |
| <kbd>Upper Arrow</kbd>  | Focus the previous week date. |
| <kbd>Down Arrow</kbd>  | Focus the next week date. |
| <kbd>Left Arrow</kbd>  | Focus the previous date. |
| <kbd>Right Arrow</kbd>  | Focus the next date. |
| <kbd>Home</kbd>  | Focus the first date in the month. |
| <kbd>End</kbd>  | Focus the last date in the month. |
| <kbd>Page Up</kbd>  | Focus the same date in the previous month. |
| <kbd>Page Down</kbd>  | Focus the same date in the next month. |
| <kbd>Enter</kbd>  | Select the currently focused date. |
| <kbd>Shift + Page Up</kbd>  | Focus the same date in the previous year. |
| <kbd>Shift + Page Down</kbd>  | Focus the same date in the previous year. |
| <kbd>Control + Upper Arrow</kbd>  | Moves into the inner level of view like month-year, year-decade |
| <kbd>Control + Down Arrow</kbd>  | Moves out from the depth level view like decade-year, year-month |
| <kbd>Control + Home</kbd>  | Focus the starting date in the current year. |
| <kbd>Control + End</kbd>  | Focus the ending date in the current year. |

Use the below list of shortcut keys to interact with the TimePicker after the TimePicker Popup has opened.

| **Press** | **To do this** |
| --- | --- |
| <kbd>Upper Arrow</kbd> | Navigate and select the previous item. |
| <kbd>Down Arrow</kbd> | Navigate and select the next item. |
| <kbd>Left Arrow</kbd> | Move the cursor towards arrow key pressed direction. |
| <kbd>Right Arrow</kbd> | Move the cursor towards arrow key pressed direction. |
| <kbd>Home</kbd> | Navigate and select the first item. |
| <kbd>End</kbd> | Navigate and select the last item. |
| <kbd>Enter</kbd> | Select the currently focused item and close the popup. |
| <kbd>Alt + Upper Arrow</kbd> | Close the popup. |
| <kbd>Alt + Down Arrow</kbd> | Open the popup. |
| <kbd>Esc</kbd> | Close the popup. |

> To focus the DateTimePicker component use the `alt+t` keys.

{% tab template="datetimepicker/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html",
es5Template="datetimepicker-accessibility-template"%}

```typescript

import { DateTimePicker } from '@syncfusion/ej2-calendars';
// creates a  DateTimePicker component
let datetimepickerObject: DateTimePicker = new DateTimePicker({
    // sets the placeholder
    placeholder: 'Select a date and time'
});
datetimepickerObject.appendTo('#element');

document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84 /* t */) {
        // press alt+t to focus the component.
        datetimepickerObject.element.focus();
    }
};

```

{% endtab %}