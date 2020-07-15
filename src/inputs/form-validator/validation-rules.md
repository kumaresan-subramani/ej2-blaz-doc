# Validation Rules

## Default Rules

The `FormValidator` has following default validation rules, which are used to validate the form.

| Rules | Description | Example |
| ------------- | ------------- | ------------- |
| `required` | The form input element must have any input values | a or 1 or - |
| `email` | The form input element must have valid `email` format values | <form@syncfusion.com> |
| `url` | The form input element must have valid `url` format values | <http://syncfusion.com/> |
| `date` | The form input element must have valid `date` format values | 05/15/2017 |
| `dateIso` | The form input element must have valid `dateISO` format values | 2017-05-15 |
| `number` | The form input element must have valid `number` format values | 1.0 or 1 |
| `digit` | The form input element must have valid `digit` values | 1 |
| `maxLength` | Input value must have less than or equal to `maxLength` character length | if `maxLength: 5`, **check** is valid and **checking** is invalid |
| `minLength` | Input value must have greater than or equal to `minLength` character length | if `minLength: 5`, **testing** is valid and **test** is invalid |
| `rangeLength` | Input value must have value between `rangeLength` character length | if `rangeLength: [4,5]`, **test** is valid and **key** is invalid |
| `range` | Input value must have value between `range` number | if `range: [4,5]`, **4** is valid and **6** is invalid |
| `max` | Input value must have less than or equal to `max` number | if `max: 3`, **3** is valid and **4** is invalid |
| `min` | Input value must have greater than or equal to `min` number | if `min: 4`, **5** is valid and **2** is invalid |
| `regex` | Input value must have valid `regex` format | if `regex: '^[A-z]+$'`, **a** is valid and **1** is invalid |

> The [`rules`](../api/form-validator#rules) option should map the input element's `name` attribute.
> The `FormValidator` library only validates the mapped input elements.

## Defining Custom Rules

You can also define custom rules in the [`rules`](../api/form-validator#rules) property and validate the form with custom logics.

The custom validation method need to return the boolean value for validating an input.

{% tab template="form-validator/form-validator2", es5Template="es5Formvalidator2" %}

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';

let customFn: (args: { [key: string]: string }) => boolean = (args: { [key: string]: string }) => {
    return args['value'].length >= 5;
};
let options: FormValidatorModel = {
    rules: {
        'user': { required: true },
        'password': { minLength: [customFn, 'Need atleast 5 letters'] }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

{% endtab %}

## Adding or Removing Rules

After creating `FormValidator` object, you can add
more rules to an input element by using [`addRules`](../api/form-validator#addrules)
method and you can also remove an existing rule from the input element by using [`removeRules`](../api/form-validator#removerules)
method.

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';

let options: FormValidatorModel = {
    rules: {
        'user': { required: true },
        'age': { number: true }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
// Add email rule to user element
formObject.addRules('user', { maxLength: 7 });
// Remove number rule from age element
formObject.removeRules('age', ['number']);
```

## Validating a Form

You can manually trigger validation by calling the [`validate`](../api/form-validator#validate)
method of [`FormValidator`](../api/form-validator).

{% tab template="form-validator/form-validator3", es5Template="es5Formvalidator3" %}

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';

let options: FormValidatorModel = {
    rules: {
        'product_name': { required: true },
        'rating': { range: [1,5] }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
// validate all input elements in the form
formObject.validate();
```

{% endtab %}

## Validating a Single Element

The [`validate`](../api/form-validator#validate) method have an optional argument, where you can pass an input element's
name attribute to validate its value against the defined rule.

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';

let options: FormValidatorModel = {
    rules: {
        'user': { required: true },
        'age': { number: true }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
// validate user element alone
formObject.validate('user');
```

## HTML5 Form Validation

HTML5 validation is the ability to `validate the user data without relying any scripts`. This is done by
using validation attributes on form elements, which allows you to specify rules for a form input like
whether a value needs to be filled In the maximum and minimum length of the data, whether it needs to be
number, an email address, or something else and pattern that it match. If the entered data follows all the
specified rules, it is considered as valid; if not, it is considered as invalid.

{% tab template="form-validator/html5-validation", es5Template="es5Html5validation" %}

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';
import { Button } from '@syncfusion/ej2-buttons';

  // Initialize Submit button
    let buttonFormValidate: Button = new Button({ isPrimary: true });
    buttonFormValidate.appendTo('#validateSubmit');

    // Initialize Reset button
    let buttonReset: Button = new Button();
    buttonReset.appendTo('#resetbtn');

    // Initialize Custom placement
    let options: FormValidatorModel = {
        customPlacement: (inputElement: HTMLElement, errorElement: HTMLElement) => {
            inputElement.parentElement.appendChild(errorElement);
        }
    };

    // Initialize Form validation
    let formObj: FormValidator;
    formObj = new FormValidator('#formId', options);
    let formId: HTMLElement = <HTMLElement>document.getElementById('formId');
    document.getElementById('formId').addEventListener('submit', (e: Event) => {
        e.preventDefault();
        if (formObj.validate()) {
            alert('Your form has been submitted.');
            formObj.reset();
        }
    });
```

{% endtab %}
