# Render palette alone

To render the `Palette` alone in ColorPicker, specify the [`mode`](../../api/color-picker#mode) property as `Palette`, and set the [`modeSwitcher`](../../api/color-picker#modeswitcher) property to `false`.

In the following sample, the [`showButtons`](../../api/color-picker#showbuttons) property is disabled to hide the control buttons and it renders only the `Palette` area.

{% tab template="colorpicker/palette", sourceFiles="app.ts,index.html,styles.css", es5Template="palette-only-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker(
        {
            //To render Palette.
            mode: 'Palette',
            // To hide modeSwitcher.
            modeSwitcher: false,
            showButtons: false
        },
        '#element');
```

{% endtab %}

>> To render `Picker` alone specify the [`mode`](../../api/color-picker#mode) property as 'Picker'.