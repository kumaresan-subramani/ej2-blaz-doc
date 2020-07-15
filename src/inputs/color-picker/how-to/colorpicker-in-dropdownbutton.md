# ColorPicker in DropDownButton

This section explains about how to render the ColorPicker in DropDownButton. The
[`target`](./../../api/drop-down-button#target) property of the DropDownButton helps to achieve this scenario. To know about the usage of `target` property refer to [`Popup templating`](./../../drop-down-button/popup-items#popup-templating) section.

In the below sample, the color picker is rendered as inline type by setting [`inline`](../../api/color-picker#inline) property as `true` and the rendered color picker wrapper is passed as a `target` to the DropDownButton to achieve the above scenario.

{% tab template="colorpicker/dropdownbtn", sourceFiles="app.ts,index.html,styles.css", es5Template="dropdownbtn-template" %}

```typescript
import { ColorPicker, ColorPickerEventArgs } from '@syncfusion/ej2-inputs';
import { DropDownButton, BeforeOpenCloseMenuEventArgs, OpenCloseMenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let colorPicker: ColorPicker = new ColorPicker(
    {
        inline: true,
        change: (args: ColorPickerEventArgs): void => {
            (ddb.element.children[0] as HTMLElement).style.backgroundColor = args.currentValue.rgba;
            closePopup();
        }
    },
    '#element');

let ddb: DropDownButton = new DropDownButton(
    {
        target: ".e-colorpicker-wrapper",
        iconCss: "e-dropdownbtn-preview",
        beforeClose: (args: BeforeOpenCloseMenuEventArgs): void => {
            args.element.parentElement.querySelector('.e-cancel').removeEventListener('click', closePopup);
        },
        open: (args: OpenCloseMenuEventArgs): void => {
            args.element.parentElement.querySelector('.e-cancel').addEventListener('click', closePopup);
        }
    },
    '#dropdownbtn');

function closePopup(): void {
    ddb.toggle();
}
```

{% endtab %}