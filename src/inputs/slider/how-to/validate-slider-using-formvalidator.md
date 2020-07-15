# Validate the slider using FormValidator

The Slider component can be validated using our [FormValidator](../../form-validator/). The following steps walk-through slider validation.

* Render slider component inside a form.
* Bind [changed](../../api/slider#changed) event in the slider component to validate the slider value when the value changes.
* Initialize and render FormValidator for the form using form ID.

```typescript

// Initialize Form validation
let formObj: FormValidator;
formObj = new FormValidator("#formId", options);

```

* Set the required property in the FormValidator [rules](../../api/form-validator#rules) collection. Here, the [min](../../api/slider#min) property of slider that sets the minimum value in the slider component is set, and it has hidden input as enable `validateHidden` property is set to true.

```typescript

// Slider element
<div id="default" name="slider"></div>

// sets required property in the FormValidator rules collection
let options: FormValidatorModel = {
  rules: {
    'default': {
      validateHidden: true,
      min: [6, "You must select value greater than 5"]
    }
  }
};

```

> Form validation is done either by ID or name value of the slider component. Above ID of the slider is used to validate it.

Using slider name: Render slider with name attribute. In the following code snippet, name attribute value of ?slider? is used for form validation.

```typescript

// Slider element
<div id="default" name="slider"></div>

// sets required property in the FormValidator rules collection
let options: FormValidatorModel = {
  rules: {
    'slider': {
      validateHidden: true,
      min: [6, "You must select value greater than 5"]
    }
  }
};

```

* Validate the form using [validate](../../api/form-validator#validate) method, and it validates the slider value with the defined rules collection and returns the result. If user selects the value less than the minimum value, form will not submit.

```typescript

formObj.validate();

```

* Slider validation can be done during value changes in slider. Refer to the following code snippet.

```typescript

// change event handler for slider
function onChanged(args: any) {
  formObj.validate();
}

```

The `FormValidator` has following default validation rules, which are used to validate the Slider component.

| Rules | Description | Example |
| ------------- | ------------- | ------------- |
| `max` | Slider component must have value less than or equal to `max` number | if `max: 3`, **3** is valid and **4** is invalid |
| `min` | Slider component must have value greater than or equal to `min` number | if `min: 4`, **5** is valid and **2** is invalid |
| `regex` | Slider component must have valid value in `regex` format | if `regex: '/4/`, **4** is valid and **1** is invalid |
| `range` | Slider component must have value between `range` number | if `range: [4,5]`, **4** is valid and **6** is invalid |

{% tab template="slider/form-validation", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="form-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
import { Button } from '@syncfusion/ej2-buttons';

// Initialize Slider component
let SliderMinObj: Slider = new Slider({
  type: 'MinRange',
  value: 30,
  ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
  changed: onMinChanged
});
SliderMinObj.appendTo("#min-slider");

// sets required property in the FormValidator rules collection
let minOptions: FormValidatorModel = {
  rules: {
    'min-slider': {
      validateHidden: true,
      min: [40, "You must select value greater than or equal to 40"]
    }
  }
};

// Initialize Form validation
let formMinObj: FormValidator;
formMinObj = new FormValidator("#formMinId", minOptions);

function onMinChanged(args: any) {
  // validate the slider value in the form
  formMinObj.validate();
}

// Initialize Slider component
let SliderMaxObj: Slider = new Slider({
  type: 'MinRange',
  value: 30,
  ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
  changed: onMaxChanged
});
SliderMaxObj.appendTo("#max-slider");

// sets required property in the FormValidator rules collection
let maxOptions: FormValidatorModel = {
  rules: {
    'max-slider': {
      validateHidden: true,
      max: [40, "You must select value less than or equal to 40"]
    }
  }
};

// Initialize Form validation
let formMaxObj: FormValidator;
formMaxObj = new FormValidator("#formMaxId", maxOptions);

function onMaxChanged(args: any) {
  // validate the slider value in the form
  formMaxObj.validate();
}

// Initialize Slider component
let SliderValObj: Slider = new Slider({
  type: 'MinRange',
  value: 30,
  ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
  changed: onValChanged
});
SliderValObj.appendTo("#val-slider");

// sets required property in the FormValidator rules collection
let valOptions: FormValidatorModel = {
  rules: {
    'val-slider': {
      validateHidden: true,
      regex: [/40/, "You must select value equal to 40"]
    }
  }
};

// Initialize Form validation
let formValObj: FormValidator;
formValObj = new FormValidator("#formValId", valOptions);

function onValChanged(args: any) {
  // validate the slider value in the form
  formValObj.validate();
}

// Initialize Slider component
let SliderRangeObj: Slider = new Slider({
  type: 'MinRange',
  value: 30,
  ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
  changed: onRangeChanged
});
SliderRangeObj.appendTo("#range-slider");

// sets required property in the FormValidator rules collection
let rangeOptions: FormValidatorModel = {
  rules: {
    'range-slider': {
      validateHidden: true,
      range: [40, 80, "You must select values between 40 and 80"]
    }
  }
};

// Initialize Form validation
let formRangeObj: FormValidator;
formRangeObj = new FormValidator("#formRangeId", rangeOptions);

function onRangeChanged(args: any) {
  // validate the slider value in the form
  formRangeObj.validate();
}

// Initialize Slider component
let SliderCustomObj: Slider = new Slider({
  type: 'Range',
  value: [30, 70],
  ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
  changed: onCustomChanged
});
SliderCustomObj.appendTo("#custom-slider");

// sets required property in the FormValidator rules collection
let customOptions: FormValidatorModel = {
  rules: {
    'custom-slider': {
      validateHidden: true,
      range: [validateRange, "You must select values between 40 and 80"]
    }
  }
};

// Initialize Form validation
let formCustomObj: FormValidator;
formCustomObj = new FormValidator("#formCustomId", customOptions);

function onCustomChanged(args: any) {
  // validate the slider value in the form
  formCustomObj.validate();
}

function validateRange(args: any) {
  return (SliderCustomObj.value as number[])[0] >= 40 && (SliderCustomObj.value as number[])[1] <= 80;
}

```

{% endtab %}