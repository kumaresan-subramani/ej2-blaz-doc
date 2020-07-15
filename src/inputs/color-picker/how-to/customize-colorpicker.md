# Customize ColorPicker

## Custom palette

By default, the Palette will be rendered with default colors. To load custom colors in the palette, specify the colors in the [`presetColors`](../../api/color-picker#presetcolors) property. To customize the color palette, add a custom class to palette tiles using [`beforeTileRender`](../../api/color-picker#beforetilerender) event.

The following sample demonstrates the above functionalities.

{% tab template="colorpicker/custom/palette", sourceFiles="app.ts,index.html,styles.css", es5Template="custom-template" %}

```typescript
import { ColorPicker, PaletteTileEventArgs, ColorPickerEventArgs } from '@syncfusion/ej2-inputs';
import { addClass, enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker({
        mode: 'Palette',
        inline: true,
        modeSwitcher: false,
        showButtons: false,
        // To specify number of columns to be rendered.
        columns: 4,
        value: '#ba68c8',
         //To load custom colors.
        presetColors: {
            'custom1': ['#ef9a9a', '#e57373', '#ef5350', '#f44336', '#f48fb1', '#f06292',
                    '#ec407a', '#e91e63', '#ce93d8', '#ba68c8', '#ab47bc', '#9c27b0', '#b39ddb',
                    '#9575cd', '#7e57c2', '#673AB7'],
            'custom2': ['#9FA8DA', '#7986CB', '#5C6BC0', '#3F51B5', '#90CAF9', '#64B5F6',
                    '#42A5F5', '#2196F3', '#81D4FA', '#4FC3F7', '#29B6F6', '#03A9F4',
                    '#80DEEA', '#4DD0E1', '#26C6DA', '#00BCD4'],
            'custom3': ['#80CBC4', '#4DB6AC', '#26A69A', '#009688', '#A5D6A7', '#81C784',
                    '#66BB6A', '#4CAF50', '#C5E1A5', '#AED581', '#9CCC65', '#8BC34A', '#E6EE9C',
                    '#DCE775', '#D4E157', '#CDDC39']
        },
        // Triggers before rendering each palette tile.
        beforeTileRender: (args: PaletteTileEventArgs): void => {
                addClass([args.element], ['e-icons', 'e-custom-tile']);
        },
        // Triggers while selecting colors from palette.
        change: (args: ColorPickerEventArgs): void => {
                document.getElementById('preview').style.backgroundColor = args.currentValue.hex;
        }
}, '#element');
```

{% endtab %}

## Hide input area from picker

By default, the input area will be rendered in ColorPicker. To hide the input area from it, add `e-hide-value` class to ColorPicker using the [`cssClass`](../../api/color-picker#cssclass) property.

In the following sample, the ColorPicker is rendered without input area.

{% tab template="colorpicker/how-to", sourceFiles="app.ts,index.html,styles.css", es5Template="hide-value-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker(
        {
            // To hide the input area
            cssClass: 'e-hide-value',
            modeSwitcher: false
        },
        '#element');
```

{% endtab %}

## Custom handle

Color picker handle shape and UI can be customized. Here, we have customized the handle as `svg icon`. The same way you can customize the handle based on your requirement.

The following sample show the customized color picker handle.

{% tab template="colorpicker/custom/handle", sourceFiles="app.ts,index.html,styles.css", es5Template="handle-template" %}

```typescript
import { ColorPicker, OpenEventArgs } from '@syncfusion/ej2-inputs';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker(
        {
            value: '#344aae',
            // To hide the input area
            cssClass: 'e-custom-picker',
            modeSwitcher: false,
            open: (args: OpenEventArgs): void => {
                args.element.querySelector('.e-handler').classList.add('e-icons');
            }
        },
        '#element');
```

{% endtab %}

## Custom primary button

By default, the applied color will be updated in primary button of the color picker. You can customize that as `icon`.

In the following sample, the `picker` icon is added to primary button and using [`change`](../../api/color-picker#change) event the selected color will be updated in bottom portion of the icon.

{% tab template="colorpicker/icon", sourceFiles="app.ts,index.html,styles.css", es5Template="icon-template" %}

```typescript
import { ColorPicker, ColorPickerEventArgs } from '@syncfusion/ej2-inputs';
import { addClass, enableRipple } from '@syncfusion/ej2-base';

let colorPicker: ColorPicker = new ColorPicker(
        {
            change: (args: ColorPickerEventArgs): void => {
                (colorPicker.element.nextElementSibling.querySelector('.e-selected-color') as HTMLElement).style.borderBottomColor = args.currentValue.rgba;
            }
        },
        '#element');

addClass([colorPicker.element.nextElementSibling.querySelector('.e-selected-color')], 'e-icons');
```

{% endtab %}

>> The Essential JS 2 provides a set of icons that can be loaded by applying `e-icons` class name to the element. You can also use third party icon to customize the primary button.

## Display hex code in input

The color picker input element can be showcased in the place of primary button. The applied color hex code will be updated in the primary button input.

The following sample shows the color picker with input.

{% tab template="colorpicker/input", sourceFiles="app.ts,index.html,styles.css", es5Template="input-template" %}

```typescript
import { ColorPicker } from '@syncfusion/ej2-inputs';
import { addClass, enableRipple } from '@syncfusion/ej2-base';

let colorPicker: ColorPicker = new ColorPicker({}, '#element');

let target: Element = colorPicker.element.nextElementSibling;
target.insertBefore(colorPicker.element, target.children[1]);
```

{% endtab %}

## Custom UI

The color picker UI can be customized in all possible ways. The following sample shows the excel like UI customization with help of SplitButton and Dialog component. In that by clicking the more colors option from color palette, the dialog contains color picker will open.

{% tab template="colorpicker/position", sourceFiles="app.ts,index.html,styles.css", es5Template="position-template" %}

```typescript
import { ColorPicker, ColorPickerEventArgs } from '@syncfusion/ej2-inputs';
import { Dialog } from '@syncfusion/ej2-popups';
import { addClass, enableRipple, EmitType } from '@syncfusion/ej2-base';
import { SplitButton, OpenCloseMenuEventArgs, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-splitbuttons';

let colorPalette: ColorPicker = new ColorPicker(
    {
        mode: 'Palette',
        inline: true,
        showButtons: false,
        modeSwitcher: false,
        change: paletteOnChange
    }
    , '#palette');

let splitBtn: SplitButton = new SplitButton(
    {
        target: '#target',
        iconCss: 'e-icons e-font-icon',
        open: (args: OpenCloseMenuEventArgs) => {
            args.element.children[1].addEventListener('click', openDialog);
        },
        beforeClose: (args: BeforeOpenCloseMenuEventArgs): void => {
            args.element.children[1].removeEventListener('click', openDialog);
        }
    }
    , '#split-btn');

let modalDialog: Dialog = new Dialog(
    {
        target: '.wrap',
        width: '270px',
        height: '336px',
        isModal: true,
        visible: false,
        cssClass: 'e-dlg-picker',
        content: '<input type="color" id="picker" />',
        animationSettings: { effect: 'Zoom' },
        open: dialogOpen,
        overlayClick: dlgClose
    }
    , '#modal-dialog');

let colorPicker: ColorPicker = new ColorPicker(
    {
        inline: true,
        modeSwitcher: false,
        change: pickerOnChange
    }
    , '#picker');

function openDialog(): void {
    modalDialog.show();
}

function dialogOpen(): void {
    colorPicker.refresh();
    colorPicker.element.nextElementSibling.querySelector('.e-ctrl-btn .e-cancel').addEventListener('click', dlgClose);
}

function dlgClose(): void {
    modalDialog.hide();
}

function paletteOnChange(args: ColorPickerEventArgs): void {
    (splitBtn.element.querySelector('.e-font-icon') as HTMLElement).style.borderBottomColor = args.currentValue.rgba;
}

function pickerOnChange(args: ColorPickerEventArgs): void {
    paletteOnChange(args);
    dlgClose();
}
```

{% endtab %}