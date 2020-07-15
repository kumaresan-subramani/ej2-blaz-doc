# Prevent nullable input in NumericTextBox

By default, the value of the NumericTextBox sets to null. In some applications, the value of the NumericTextBox should not be null at any instance. In such cases, following sample can be used to prevent nullable input in NumericTextBox.

{% tab template="numeric-textbox/nullable-input", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-nullable-input-template" %}

```typescript

import {NumericTextBox} from '@syncfusion/ej2-inputs';

// initializes NumericTextBox component
let numeric: NumericTextBox = new NumericTextBox({
    // sets value to the NumericTextBox
    placeholder: 'NumericTextbox',
    floatLabelType: 'Always' ,
    // prevents nullable value during initialization
    created: function (args) {
        if (this.value==null) {
            this.value=0;
        }
     },
   blur: function (args) {
        // checks for nullable value while focus out
            if (args.value==null)
              numeric1.value=0;
    }
 });

// renders initialized NumericTextBox
numeric.appendTo('#numeric1');

 ```

{% endtab %}