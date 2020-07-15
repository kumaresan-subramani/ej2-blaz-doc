# Customize the step value and hide spin buttons

The spin buttons allow you to increase or decrease the value with the predefined [`step`](../../api/numerictextbox#step)
value. The visibility of spin buttons can be set using the[`showSpinButton`](../../api/numerictextbox#showspinbutton) property.

{% tab template="numeric-textbox/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="numeric-hidespin-template" %}

```typescript

import {NumericTextBox} from '@syncfusion/ej2-inputs';

let hideButtons: NumericTextBox = new NumericTextBox({
        // sets the step value as '2' to increase/decrease the value by '2'
        step: 2,
        // sets the showSpinButton value as `false` to hide the spin buttons
        showSpinButton: false
        min: 10,
        max: 100,
        value: 16
    });

hideButtons.appendTo('#numeric');

```

{% endtab %}