---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Client side validation

To achieve the client side validation in a DatePicker component by using
[Essential JavaScript 2 FormValidator](../../form-validator/). It provides an option to customize the feedback error messages to the corresponding
fields to take action to resolve the issue.

In this below example, the required field validation is implemented by mapping
the name attribute
value to the rules property. It will validate the DatePicker component and display the validation
message when the textbox value is empty during form post back or focus out.

{% tab template="datepicker/form-validator" , sourceFiles="app.ts,index.html" ,
es5Template="datepicker-validation-template" %}

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
// creates datepicker with readonly.
let datepickerObject: DatePicker = new DatePicker({
    // sets the palceholder property.
    placeholder: 'Enter date',
    // sets the value
    value: new Date()
});
datepickerObject.appendTo('#element');

let options: FormValidatorModel = {
    rules: {
        'datevalue': { required: true }
    },
    customPlacement: function (inputElement, errorElement) {
        //to place the error message in custom position.
        (<HTMLElement>inputElement).parentElement.parentElement.appendChild(errorElement);
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

{% endtab %}