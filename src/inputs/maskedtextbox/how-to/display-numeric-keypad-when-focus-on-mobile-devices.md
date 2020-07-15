# Display numeric keypad when focus on mobile devices

By default, on focusing the MaskedTextBox, alphanumeric keypad will be displayed on mobile devices. Sometimes only numeric keypad for number values is needed, and this can be achieved by setting "type" property to `tel`.

Refer to the following example to enable numeric keypad in MaskedTextBox.

{% tab template="maskedtextbox/numeric", sourceFiles="app.ts,index.html,styles.css", es5Template="cursor-template" %}

```typescript

import { MaskedTextBox } from '@syncfusion/ej2-inputs';

// initializes the MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox({
    // sets mask format to the MaskedTextBox
    mask: '999-99999',
    value: "342-45432",
});

mask.appendTo('#mask1');

 ```

{% endtab %}