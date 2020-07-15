---
title: "How To"
component: "Calendar"
description: "Miscellaneous aspects of customizing the calendar"
---

# Set clear button

To configure `clear` button in Calendar UI, do the following:

1. To the [`created`](../../api/calendar#created)
 event of the Calendar, add the required elements to make clear button visible. In the following
 example, Essential JS 2 button component within `div` element is used.

2. When the `e-footer` class is used, the div tag acts as the footer.

3. Using these button, selected date can be cleared.

4. Bind the required event handler to the button tags to update the value.

Code example is as follows:

{% tab template="calendar/how-to", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css"
,es5Template="calendar-btn-template"%}

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
// creates a Calendar with today and clear buttons.
let calendarObject: Calendar = new Calendar({
    created: onCreate
});
calendarObject.appendTo('#element');
function onCreate() {
    //creates the custom element for clear button.
    let clearBtn: HTMLElement = document.createElement('button');
    let footerElement: HTMLElement = document.getElementsByClassName('e-footer-container')[0];
    clearBtn.className = 'e-btn e-clear e-flat';
    clearBtn.textContent = 'Clear';
    footerElement.prepend(clearBtn);
    this.element.appendChild(footerElement);
}
// custom click handler to update the value property with current date object.
document.querySelector('.e-footer-container .e-clear').addEventListener('click', function () {
    calendarObject.value = new Date();
    calendarObject.dataBind();
});
```

{% endtab %}
