# Perform custom validation using FormValidator

To perform custom validation on the MaskedTextBox use the FormValidator along with custom validation rules.

In the following example, the MaskedTextBox is validated for invalid mobile number by adding custom validation in the rules collection of the FormValidator.

{% tab template="maskedtextbox/custom-validation", sourceFiles="app.ts,index.html,styles.css", es5Template="mask-prompt-template" %}

```typescript

import { MaskedTextBox } from '@syncfusion/ej2-inputs';
import { Button } from '@syncfusion/ej2-buttons';
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';

// initializes the MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox({
    // sets mask format to the MaskedTextBox
    mask: '000-000-0000',
    placeholder: 'Mobile Number',
    floatLabelType: 'Always'
});

mask.appendTo('#mask1');

//initialize button
let button: Button = new Button();
button.appendTo('#submit_btn');

// checks the length of mask value and returns corresponding boolean value
let customFn: (args: { [key: string]: string }) => boolean = (args: { [key: string]: string }) => {
    let argsLength:number = args.element.ej2_instances[0].value.length;
    if(argsLength != 0) {
        return argsLength >= 10;
    } else {
        return true;
    }
};

//value is returned based on the length of mask
let custom: (args: { [key: string]: string }) => boolean = (args: { [key: string]: string }) => {
    let argsLength:number = args.element.ej2_instances[0].value.length;
    if(argsLength == 0) {
        return 0;
    } else {
        return argsLength;
    }
};

// sets required property in the FormValidator rules collection
let options: FormValidatorModel = {
    rules: {
        'mask_value': { numberValue: [customFn, 'Enter valid mobile number'] },
    },
}

// defines FormValidator to validate the MaskedTextBox
let formObject: FormValidator = new FormValidator('#form-element', options);

//FormValidator rule is added for empty MaskedTextBox
formObject.addRules('mask_value', { maxLength: [custom, 'Enter mobile number'] });

// places error label outside the MaskedTextBox using the customPlacement event of FormValidator
let customPlace: (element: HTMLElement, error: HTMLElement) => void = (element: HTMLElement, error: HTMLElement) => {
    document.querySelector(".form-group").appendChild(error);
};

formObject.customPlacement = customPlace;

document.getElementById('submit_btn').onclick = () => {
    // validates the MaskedTextBox
    formObject.validate("mask_value");
    let ele: HTMLInputElement = <HTMLInputElement>document.getElementById('mask1');
    // checks for incomplete value and alerts the format submit
    if (ele.value !== "" && ele.value.indexOf(mask.promptChar) === -1) {
        alert("Submitted");
    }
};

 ```

{% endtab %}