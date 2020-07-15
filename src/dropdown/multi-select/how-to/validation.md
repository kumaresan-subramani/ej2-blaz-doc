---
title: "Multiselect validation"
component: "MultiSelect"
description: "This section demonstrates the validation support of the Syncfusion JavaScript multiselect control."
---

# Validate MultiSelect

MultiSelect component inside form can be validated through `FormValidator`. Add the name attribute of component to be validated inside rules of FormValidator. Error message after validation can be placed in DOM based on the requirement through customPlacement.

In the following sample, validation is added for MultiSelect component.

{% tab template="multiselect/validation", es5Template="validation-howto", sourceFiles ='app.ts,index.html,styles.css' %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
import { Button } from '@syncfusion/ej2-buttons';
import { MultiSelect } from '@syncfusion/ej2-dropdowns';

   let listObj1: MultiSelect = new MultiSelect({
        // set the placeholder to MultiSelect input element
        placeholder: 'Favorite Sports',
        // set the type of mode for how to visualized the selected items in input element.
        mode: 'Default'
    });
    listObj1.appendTo('#default');

    // Initialize Submit button
    let buttonFormValidate: Button = new Button({ isPrimary: true });
    buttonFormValidate.appendTo('#validateSubmit');
    // Initialize Reset button
    let buttonReset: Button = new Button({});
    buttonReset.appendTo('#resetbtn');
    // Initialize Custom placement
    let option: FormValidatorModel = {
        rules: {
            // Initialize the CustomPlacement.
             default: { required: true }
        },
    customPlacement: (inputElement: HTMLElement, error: HTMLElement)=>{
        inputElement.parentElement.parentElement.parentElement.insertBefore(error, inputElement.parentElement.parentElement.nextSibling);
    }
    };
    // Initialize Form validation
    let formObj: FormValidator;
    formObj = new FormValidator('#formId', option);
    let formId: HTMLElement = <HTMLElement>document.getElementById('formId');
    document.getElementById('formId').addEventListener(
        'submit',
        (e: Event) => {
            e.preventDefault();
            if (formObj.validate()) {
                alert('Success');
                formObj.reset();
            }
        });

```

{% endtab %}