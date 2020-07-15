# Form Validator

The [`FormValidator`](../api/form-validator) can be used to validate the form elements before submitting to the server.
That is, when typing wrong input values in the form element, it will show an alert message to notify
the correction about the mistakes and it won't allow to submit the form until the input gets correct value.

{% tab template="form-validator/form-validator1", es5Template="es5Formvalidator1" %}

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';
let options: FormValidatorModel = {
    rules: {
        'user': { required: true },
        'age': { number: true, max: 25 }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

{% endtab %}

## Validation Rules

### Default Rules

The `FormValidator` has following default validation rules, which are used to validate the form.

| Rules | Description | Example |
| ------------- | ------------- | ------------- |
| `required` | The form input element must have any input values | a or 1 or - |
| `email` | The form input element must have valid `email` format values | `<form@syncfusion.com>` |
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

### Defining Custom Rules

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

### Adding or Removing Rules

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

You can manually trigger validation by calling the [`validate`](../api/form-validator)
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

## Error Messages

The `FormValidator` provides default error messages for all default validation rules.
It is tabulated as follows

| Rules | message |
| ------------- | ------------- |
| `required` | This field is required. |
| `email` | Please enter a valid email address. |
| `url` | Please enter a valid URL. |
| `date` | Please enter a valid date. |
| `dateIso` | Please enter a valid date ( ISO ). |
| `number` | Please enter a valid number. |
| `digit` | Please enter only digits. |
| `maxLength` | Please enter no more than {0} characters. |
| `minLength` | Please enter at least {0} characters. |
| `rangeLength` | Please enter a value between {0} and {1} characters long. |
| `range` | Please enter a value between {0} and {1}. |
| `max` | Please enter a value less than or equal to {0}. |
| `min` | Please enter a value greater than or equal to {0}. |
| `regex` | Please enter a correct value. |

### Customizing Error Messages

The default error message for a rule can be customizable by defining it along with concern rule object as follows.

{% tab template="form-validator/form-validator2", es5Template="es5Formvalidator2" %}

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';

let options: FormValidatorModel = {
    rules: {
        'user': { required: true },
        'password': { minLength: [6, 'Need atleast 6 character length'] }
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

{% endtab %}

### Customizing Error Placement

The `FormValidator` has an event [`customPlacement`](../api/form-validator#customplacement) which can be used to place
the error message from default position to desired custom location.

{% tab template="form-validator/form-validator4", es5Template="es5Formvalidator4" %}

```typescript
import {FormValidator, FormValidatorModel} from '@syncfusion/ej2-inputs';

let options: FormValidatorModel = {
    rules: {
        'user': { required: [true, 'User Name: required'] },
        'password': { minLength: [5, 'Password: need atleast 5 characters'] }
    },
    customPlacement: (inputElement: HTMLElement, error: HTMLElement)=>{
        document.getElementById('error').appendChild(error);
    }
}
let formObject: FormValidator = new FormValidator('#form-element', options);
```

{% endtab %}