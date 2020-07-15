# Customize the limits

Slider appearance can be customized via CSS. By overriding the slider CSS classes, the slider limit bar can be customized. Here, the limit bar is customized with different background color. By default, the slider has class `e-limits` for limits bar. You can override the class with our own color values as given in the following code snippet.

```css
.e-slider-container.e-horizontal .e-limits {
     background-color: rgba(69, 100, 233, 0.46);
}
```

{% tab template="slider/limit-customization", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="limit-customization" %}

```typescript
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { Slider, NumericTextBox, ChangeEventArgs } from '@syncfusion/ej2-inputs';
import { CheckBox, ChangeEventArgs as CheckBoxChange } from '@syncfusion/ej2-buttons';

// tslint:disable-next-line:max-func-body-length

    // Initialize slider control
    let minrangeObj: Slider = new Slider({
        // Set slider minimum and maximum values
        min: 0, max: 100,
        // Set the value for slider
        value: 30,
        // Set the step value
        step: 1,
        // Initialize ticks with placement, largestep, smallstep
        ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
        // Set the type for slider
        type: 'MinRange',
        // Set the limit values for the slider
        limits: { enabled: true, minStart: 10, minEnd: 40 },
        // Initialize tooltip with placement and showOn
        tooltip: { isVisible: true, placement: 'Before', showOn: 'Focus' }
    });
    minrangeObj.appendTo('#minrange');

    // Initialize slider control
    let rangeObj: Slider = new Slider({
        // Set slider minimum and maximum values
        min: 0, max: 100,
        // Set the initial range values for slider
        value: [30, 70],
        // Set the step value
        step: 1,
        // Set the type to render range slider
        type: 'Range',
        // Initialize ticks with placement, largestep, smallstep
        ticks: { placement: 'Before', largeStep: 20, smallStep: 5, showSmallTicks: true },
        // Set the limit values for the slider
        limits: { enabled: true, minStart: 10, minEnd: 40, maxStart: 60, maxEnd: 90 },
        // Initialize tooltip with placement and showOn
        tooltip: { isVisible: true, placement: 'Before', showOn: 'Focus' }
    });
    rangeObj.appendTo('#range');

    // Initialize NumericTextBox
    let minStart: NumericTextBox = new NumericTextBox({
        value: 10,
        min: 0,
        max: 100,
        change: minStartChange
    });
    minStart.appendTo('#minStart');

    let minEnd: NumericTextBox = new NumericTextBox({
        value: 40,
        min: 0,
        max: 100,
        change: minEndChange
    });
    minEnd.appendTo('#minEnd');

    let maxStart: NumericTextBox = new NumericTextBox({
        value: 60,
        min: 0,
        max: 100,
        change: maxStartChange
    });
    maxStart.appendTo('#maxStart');

    let maxEnd: NumericTextBox = new NumericTextBox({
        value: 90,
        min: 0,
        max: 100,
        change: maxEndChange
    });
    maxEnd.appendTo('#maxEnd');

    // Initialize Checkbox
    let fixedOne: CheckBox = new CheckBox({ change: fixOne });
    fixedOne.appendTo('#fixedOne');

    let fixedSecond: CheckBox = new CheckBox({ change: fixSecond });
    fixedSecond.appendTo('#fixedSecond');

    // Eventlisteners to lock first handle of the both sliders
    function fixOne(args: CheckBoxChange): void {
        minrangeObj.limits.startHandleFixed = args.checked;
        rangeObj.limits.startHandleFixed = args.checked;
    }

    // Eventlisteners to lock second handle of the both sliders
    function fixSecond(args: CheckBoxChange): void {
        minrangeObj.limits.endHandleFixed = args.checked;
        rangeObj.limits.endHandleFixed = args.checked;
    }

    // Eventlisteners to change limit values for both sliders
    function minStartChange(args: ChangeEventArgs): void {
        minrangeObj.limits.minStart = args.value;
        rangeObj.limits.minStart = args.value;
    }

    function minEndChange(args: ChangeEventArgs): void {
        minrangeObj.limits.minEnd = args.value;
        rangeObj.limits.minEnd = args.value;
    }

    function maxStartChange(args: ChangeEventArgs): void {
        minrangeObj.limits.maxStart = args.value;
        rangeObj.limits.maxStart = args.value;
    }

    function maxEndChange(args: ChangeEventArgs): void {
        minrangeObj.limits.maxEnd = args.value;
        rangeObj.limits.maxEnd = args.value;
    }
```

{% endtab %}
