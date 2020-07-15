---
title: "Localization"
component: "FromValidator"
description: "Localization support in FromValidator"
---

# Localization

The [`Localization`](../common/localization/) library allows users to localize the default error message contents of the `formValidator` to different cultures using the `locale` property.

The FormValidator provides default error messages for all default validation rules. It is tabulated as follows:

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

## Loading translations

To load translation object in your application use `load` function of `L10n` class.

The following example demonstrates the FormValidator in `Arabic` culture with error message for email.

{% tab template="form-validator/form-validator5", es5Template="es5Formvalidator5" %}

```typescript

import { FormValidator,FormValidatorModel} from '@syncfusion/ej2-inputs';
import { L10n } from '@syncfusion/ej2-base';

// Load `German` culture to override spin buttons tooltip text
L10n.load({
    'ar-AR': {
        'formValidator':{
            "required" : "هذه الخانة مطلوبه",
            "email": "أدخل بريد إلكتروني صالح",
            "url": "أدخل رابط صحيح من فضلك",
            "date": "ارجوك ادخل تاريخ صحيح.",
            "dateIso": "الرجاء إدخال تاريخ صالح (ISO)",
            "creditcard": "يرجى إدخال رقم بطاقة صالح",
            "number" : "من فضلك أدخل رقما صالحا",
            "digits" : "الرجاء إدخال الأرقام فقط",
            "maxLength" : "الرجاء إدخال ما لا يزيد عن {0} حرف",
            "minLength": "الرجاء إدخال أحرف {0} على الأقل",
            "rangeLength" : "يرجى إدخال قيمة بين {0} و {1} من الأحرف",
            "range" : "يرجى إدخال قيمة بين {0} و {1}",
            "max" : "الرجاء إدخال قيمة أقل من أو تساوي {0}",
            "min" : "الرجاء إدخال قيمة أكبر من أو تساوي {0}",
            "regex": "يرجى إدخال قيمة صحيحة",
            "tel" : "يرجى إدخال رقم هاتف صالح",
            "pattern" : "الرجاء إدخال قيمة نمط صحيح",
            "equalTo" : "يرجى إدخال نص مطابقة صحيح"
        }
    },

});

let options: FormValidatorModel = {
    rules: {
        email: { email: true },
    },
    locale:"ar-AR"
}
let formObject: FormValidator = new FormValidator('#form-element', options);

```

{% endtab %}