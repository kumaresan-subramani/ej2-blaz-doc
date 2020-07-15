# Handle no color support

The ColorPicker component supports no color functionality. By clicking the no color tile from palette, the selected color becomes `empty` and considered as no color has been selected from color picker.

## Default no color

To achieve this, set [`noColor`](../../api/color-picker#nocolor) property as `true`.

In the following sample, the first tile of the color palette represents the no color tile. By clicking the no color tile you can achieve the above functionalities.

{% tab template="colorpicker/no-color/default", sourceFiles="app.ts,index.html,styles.css", es5Template="default-template" %}

```typescript
import { ColorPicker, ColorPickerEventArgs } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

let preview: HTMLElement = document.getElementById('preview');

let colorPicker: ColorPicker = new ColorPicker(
    {
        mode: "Palette",
        value: "#ba68c8",
        showButtons: false,
        modeSwitcher: false,
        //To enable no color support
        noColor: true,
        change: (args: ColorPickerEventArgs): void => {
                    preview.style.backgroundColor = args.currentValue.hex;
                    preview.textContent = args.currentValue.hex ? args.currentValue.hex : 'No color';
                }
    },
    '#element');

preview.style.backgroundColor = "#ba68c8";
preview.textContent = "#ba68c8";
```

{% endtab %}

## Custom no color

The following sample show the color palette with custom no color option.

{% tab template="colorpicker/no-color/custom", sourceFiles="app.ts,index.html,styles.css", es5Template="custom-template" %}

```typescript
import { ColorPicker, ColorPickerEventArgs, PaletteTileEventArgs } from '@syncfusion/ej2-inputs';
import { SplitButton } from '@syncfusion/ej2-splitbuttons';

let preview: HTMLElement = document.getElementById('preview');

let colorPicker: ColorPicker = new ColorPicker(
    {
        mode: "Palette",
        value: "#f44336",
        showButtons: false,
        modeSwitcher: false,
        inline: true,
        columns: 4,
        presetColors: { 'custom': ['#f44336', '#e91e63', '#9c27b0', '#673ab7', '#2196f3', '#03a9f4', '#00bcd4', '#009688', '#8bc34a', '#cddc39', '#ffeb3b', '#ffc107'] },
        beforeTileRender: (args: PaletteTileEventArgs): void => {
            args.element.classList.add('e-custom-tile');
        },
        change: (args: ColorPickerEventArgs): void => {
                    (document.querySelector(".e-split-btn .e-picker-icon") as HTMLElement).style.borderBottomColor = args.currentValue.hex;
                    preview.style.backgroundColor = args.currentValue.hex;
                    preview.textContent = args.currentValue.hex;
                    if (splitBtn.element.getAttribute("aria-expanded")) {
                        splitBtn.toggle();
                        splitBtn.element.focus();
                    }
                }
    },
    '#element');

let splitBtn: SplitButton = new SplitButton({ iconCss: "e-cp-icons e-picker-icon", target: "#target" }, '#splitbtn')

preview.style.backgroundColor = "#f44336";
preview.textContent = "#f44336";

document.getElementById('no-color').onclick = (): void => {
    //sets color picker value property to null
    colorPicker.setProperties({ 'value': "" }, true);
    (document.querySelector('.e-split-btn .e-picker-icon')as HTMLElement).style.borderBottomColor = "transparent";
    preview.textContent = "No color"
    preview.style.backgroundColor = "transparent";
}
```

{% endtab %}