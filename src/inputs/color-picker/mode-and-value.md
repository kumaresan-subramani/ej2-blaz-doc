---
title: "ColorPicker Mode and Value"
component: "ColorPicker"
description: "TypeScript ColorPicker component has two different modes and allows the user to specify color value to the ColorPicker."
---

# Mode and Value

## Rendering palette at initial load

By default, the `Picker` area will be rendered at initial load. To render the Palette area while opening the ColorPicker pop-up, and specify the [`mode`](../api/color-picker#mode) property as `Palette`.

In the following sample, it will render the `Palette` at initial load.

{% tab template="colorpicker/palette", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", es5Template="palette-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker({
        //To render palette at initial load.
        mode: 'Palette'
}, '#element');
```

{% endtab %}

## Color value

The [`value`](../api/color-picker#value) property can be used to specify the color value to the ColorPicker.
It supports either `three` or `six` digit hex codes. To include `opacity`, set the color value as `four` or `eight`
digit hex code.

In the following sample, the color value sets as `four` digit hex code, the last digit represents the `opacity` value.

{% tab template="colorpicker/value", sourceFiles="app.ts,index.html,styles.css", es5Template="value-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker({
        //To set color value.
        value: '035a',
        mode: 'Picker',
        modeSwitcher: false
}, '#element');
```

{% endtab %}

>> The [`value`](../api/color-picker#value) property supports hex code with or without `#` prefix.

## See Also

* [How to render palette alone](./how-to/render-palette-alone)
* [Custom palette](./how-to/customize-colorpicker#custom-palette)
* [No color support in palette](./how-to/handle-no-color-support)