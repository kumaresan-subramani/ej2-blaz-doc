---
title: "How To"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the time picker"
---

# Client side validation using FormValidator

To achieve client side validation in a TimePicker component, use
[Essential JavaScript 2 FormValidator](../../form-validator/). It provides an option to customize feedback error messages to the corresponding
fields for taking action and resolving the issue.

In the following example, the required field validation is implemented by mapping the name attribute
value to the rules property. It validates the TimePicker component and displays the validation
message when the textbox value is empty during form post back or focus out.

{% tab template="timepicker/validation" , sourceFiles="app.ts,index.html" ,es5Template="timepicker-validation-template"%}

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
//import the form validator related functions
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);


let timeObject: TimePicker = new TimePicker({
    placeholder: 'Select Time'
});
timeObject.appendTo('#element');

let options: FormValidatorModel = {
    rules: {
        //must specify the name attribute value in rules section
        'timevalue': { required: true }
    },
    customPlacement: (inputElement: HTMLElement, errorElement: HTMLElement) => {
        //to place the error message in custom position
        //inputElement - target element where the error text will be appended
        //errorElement - error text which will be displayed.
        inputElement.parentElement.parentElement.appendChild(errorElement);
    }
};
let formObject: FormValidator = new FormValidator('#form-element', options);

```

{% endtab %}
