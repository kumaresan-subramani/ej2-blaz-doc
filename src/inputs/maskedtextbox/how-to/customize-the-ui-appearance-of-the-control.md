# Customize the UI appearance of the control

The appearance of the MaskedTextBox can be changed by adding custom `cssClass` to the component and enabling styles.

Refer to the following example to change the appearance of the MaskedTextBox.

{% tab template="maskedtextbox/custom css", sourceFiles="app.ts,index.html,styles.css", es5Template="cursor-template" %}

```typescript

import { MaskedTextBox } from '@syncfusion/ej2-inputs';

// initializes the MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox({
    // sets mask format to the MaskedTextBox
    mask: '00000',
    value: "42648",
    placeholder: 'Enter User ID',
    floatLabelType: 'Always',
    cssClass: 'e-style',
    focus: function(args) {
        //sets cursor position at start of MaskedTextBox
        args.selectionEnd= args.selectionStart;
    }
});

mask.appendTo('#mask1');

 ```

{% endtab %}