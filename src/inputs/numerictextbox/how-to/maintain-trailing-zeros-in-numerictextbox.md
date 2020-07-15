# Maintain trailing zeros in NumericTextBox

By default, trailing zeros disappear when the NumericTextBox gets focus. However, you can use the following sample to maintain the trailing zeros while focusing the NumericTextBox.

{% tab template="numeric-textbox/trailing-zeros", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-trailing-zero-template" %}

```typescript

import {NumericTextBox} from '@syncfusion/ej2-inputs';
//maintains trailing zeros while focusing
let numericFocus: function () {
    var numericObj = this.ej2_instances ? this.ej2_instances[0] : this;
    numericObj.element.value = numericObj.formattedValue(numericObj.decimals, +numericObj.element.value);
}
// Render the Numeric Textbox
let numeric: NumericTextBox = new NumericTextBox({
    value: 10,
    decimals:2,
    format: 'n2',
    placeholder: 'NumericTextbox',
    floatLabelType: 'Always' ,
    change: numericFocus
});
numeric.appendTo('#numeric');
document.getElementById('numeric').addEventListener('focus', numericFocus);

 ```

{% endtab %}
