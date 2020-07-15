# Disabled

To achieve disabled state in ColorPicker, set the [`disabled`](../../api/color-picker#disabled) property to `true`. The ColorPicker pop-up cannot be accessed in disabled state.

The following example shows the `disabled` state of ColorPicker component.

{% tab template="colorpicker/disabled", sourceFiles="app.ts,index.html,styles.css", es5Template="disabled-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker({ disabled: true }, '#element');
```

{% endtab %}