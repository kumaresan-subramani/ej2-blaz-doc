# Hide control buttons

ColorPicker can be rendered without control buttons (Apply/Cancel). In this case, while selecting a color, the ColorPicker pop-up is closed and selected colors can be applied directly. To hide control buttons, set the [`showButtons`](../../api/color-picker#showbuttons) property to `false`.

{% tab template="colorpicker/how-to", sourceFiles="app.ts,index.html,styles.css", es5Template="hide-ctrlbtn-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker({
    //To hide control buttons.
    showButtons: false
}, '#element');
```

{% endtab %}