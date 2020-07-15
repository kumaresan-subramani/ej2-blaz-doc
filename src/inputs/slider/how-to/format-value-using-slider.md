# Format value using slider

## Achieve date format

The date formatting can be achieved in `ticks` and `tooltip` using `renderingTicks` and `tooltipChange` events, respectively. The process of formatting is explained in the following sample.

{% tab template="slider/date-format", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="format-template"  %}

```typescript

import { Slider, SliderTickEventArgs, SliderTooltipEventArgs } from '@syncfusion/ej2-inputs';

// Initialize slider control
 let dateObj: Slider = new Slider({

    /**
     * Initialize the min and max values of the slider using JavaScript date functions
     * new Date (Year, Month, day, hours, minutes, seconds, milliseconds)
     */

    min: new Date("2013-06-13").getTime(),
    value: new Date("2013-06-15").getTime(),
    max: new Date("2013-06-21").getTime(),
    // 86400000 milliseconds for a day
    step: 86400000,
    tooltipChange: function (args: SliderTooltipEventArgs) {
        let totalMiliSeconds = Number(args.text);
        // Convert the current milliseconds to the respective date in desired format
        let custom = { year: "numeric", month: "short", day: "numeric" };
        args.text = new Date(totalMiliSeconds).toLocaleDateString("en-us", custom);
    },
    tooltip: {
        placement: 'Before',
        isVisible: true
    },
    renderingTicks: function (args: SliderTickEventArgs) {
        let totalMiliSeconds = Number(args.value);
        // Convert the current milliseconds to the respective date in desired format
        let custom = { year: "numeric", month: "short", day: "numeric" };
        args.text = new Date(totalMiliSeconds).toLocaleDateString("en-us", custom);
    },
    ticks: {
        placement: 'After',
        // 2 * 86400000 milliseconds for two days
        largeStep: 2 * 86400000
    },
    showButtons: true
});
// Render initialized Slider
dateObj.appendTo('#slider');

```

{% endtab %}

## Achieve time format

The time formatting can be achieved in the same manner as date formatting using `renderingTicks` and `change` events. The process of time formatting is
explained in the following sample.

{% tab template="slider/time-format", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="time-format"  %}

```typescript

import { Slider, SliderTickEventArgs, SliderTooltipEventArgs } from '@syncfusion/ej2-inputs';

// Initialize slider control
 let timeObj: Slider = new Slider({
    /**
     * Initialize the min and max values of the slider using JavaScript date functions
     * new Date (Year, Month, day, hours, minutes, seconds, milliseconds)
     */

    min: new Date(2013, 6, 13, 11).getTime(),
    max: new Date(2013, 6, 13, 17).getTime(),
    value: new Date(2013, 6, 13, 13).getTime(),
    // 3600000 milliseconds = 1 Hour
    step: 3600000,
    tooltipChange: function (args: SliderTooltipEventArgs) {
        let totalMiliSeconds = Number(args.text);
        let custom = { hour: '2-digit', minute: '2-digit' };
        args.text = new Date(totalMiliSeconds).toLocaleTimeString("en-us", custom);
    },
    tooltip: {
        placement: 'Before',
        isVisible: true
    },
    renderingTicks: function (args: SliderTickEventArgs) {
        let totalMiliSeconds = Number(args.value);
        let custom = { hour: '2-digit', minute: '2-digit' };
        args.text = new Date(totalMiliSeconds).toLocaleTimeString("en-us", custom);
    },
    ticks: {
        placement: 'After',
        // 2 * 3600000 milliseconds = 2 Hour
        largeStep: 2 * 3600000
    },
    showButtons: true
});
// Render initialized slider
timeObj.appendTo('#slider');

```

{% endtab %}

## Customize numeric Value

The numeric values can be formatted into different decimal digits or fixed number of whole numbers or to represent units. The numeric processing is demonstrated as follows.

{% tab template="slider/how-to", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="how-to" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize slider control
 let kilometerObj: Slider = new Slider({
    min: 0, max: 100, step: 1, value: 30,
    // Apply two decimal specifiers formatting if any decimal values are processed with 'Km' text appended to the value
    tooltip: { isVisible: true, format: '##.## Km' },
    // Apply two decimal specifiers formatting if any decimal values are processed with 'Km' text appended to the value
    ticks: { placement: 'After', format: '##.## Km', largeStep: 20, smallStep: 10, showSmallTicks: true }
});
// Render initialized slider
kilometerObj.appendTo('#slider');

// Initialize slider control
 let decimalObj: Slider = new Slider({
    min: 0.1, max: .2, step: 0.01, value: 0.13,
    // Apply three decimal specifiers formatting if any decimal values are processed then reset will be appened with two zero
    tooltip: { isVisible: true, format: '##.#00' },
    // Apply three decimal specifiers formatting if any decimal values are processed then reset will be appened with two zero
    ticks: { placement: 'After', format: '##.#00', largeStep: 0.02, smallStep: 0.01, showSmallTicks: true }
});
// Render initialized slider
decimalObj.appendTo('#slider1');

// Initialize slider control
 let sliderObj: Slider = new Slider({
    min: 0, max: 100, step: 1, value: 30,
    // Apply numberic formatting with two leading zero for tooltip
    tooltip: { isVisible: true, format: '00##' },
    // Apply numberic formatting with two leading zero for ticks
    ticks: { placement: 'After', format: '00##', largeStep: 20, smallStep: 10, showSmallTicks: true }
});
// Render initialized slider
sliderObj.appendTo('#slider2');

```

{% endtab %}