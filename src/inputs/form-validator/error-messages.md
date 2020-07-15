# Error Messages

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

## Customizing Error Messages

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

## Customizing Error Placement

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