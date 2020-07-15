# Customize the UI appearance of the control

You can change the appearance of the NumericTextBox by adding custom `cssClass` to the component and enabling styles. Refer to the following example to change the appearance of the NumericTextBox.

{% tab template="numeric-textbox/custom-css", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-custom-template" %}

```typescript

import { NumericTextBox } from '@syncfusion/ej2-inputs';

// initializes the NumericTextBox component
let numeric: NumericTextBox = new NumericTextBox({
    // sets value to the NumericTextBox
    value: 10,
    placeholder: 'Enter value ',
    floatLabelType: 'Always',
    //adding custom css class to NumericTextBox
    cssClass: 'e-style'
});

// renders initialized NumericTextBox
numeric.appendTo('#numeric1');

 ```

{% endtab %}