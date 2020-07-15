# Customize the ticks

Slider view can be customized via CSS. By overriding the slider CSS classes, you can customize the ticks. The ticks in slider allows you to easily identify the current value/values of the slider. It contains [`smallStep`](../../api/slider/ticksData/#smallstep) and [`largeStep`](../../api/slider/ticksData/#largestep). By default, slider has class `e-tick` for slider ticks. You can override the class as per your requirement. Refer to the following code snippet to render ticks.

```typescript
.e-scale .e-tick.e-custom::before {
    content: '\e967';
    position: absolute;
}
```

Here, the color for rendered ticks has been applied through nth-child(`child_number`). The color is applied to the value of the `child_number` in the slider.

```typescript
#ticks_slider .e-scale :nth-child(1)::before {
    color: red;
}
```

{% tab template="slider/ticks-customization", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="ticks-customization" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { Slider, SliderTickRenderedEventArgs, SliderTickEventArgs } from '@syncfusion/ej2-inputs';

    // Initialize slider component
    let ticksSlider: Slider = new Slider({
        // Set slider minimum and maximum values
        min: 0, max: 100,
        // Set the initial value for slider
        value: 30,
        // Set the step value for slider
        step: 5,
        // Set the type to render minRange slider
        type: 'MinRange',
        // Initialize ticks with placement, largestep
        ticks: { placement: 'Before', largeStep: 20 },
        // Handler used to add custom class to all tick element
        renderingTicks: (args: SliderTickEventArgs) => {
            if (args.tickElement.classList.contains('e-large')) {
                args.tickElement.classList.add('e-custom');
            }
        }
    });
    ticksSlider.appendTo('#ticks_slider');

    // Initialize slider component
    let customTicks: Slider = new Slider({
        // Set slider minimum and maximum values
        min: 0, max: 100,
        // Set the initial value for slider
        value: 30,
        // Set the type to render minRange slider
        type: 'MinRange',
        // Initialize ticks with placement, largestep, smallstep
        ticks: { placement: 'Both', largeStep: 20, smallStep: 5 },
        // Handler used to customize tick element
        renderedTicks: (args: SliderTickRenderedEventArgs) => {
            let li: any = args.ticksWrapper.getElementsByClassName('e-large');
            let remarks: any = ['Very Poor', 'Poor', 'Average', 'Good', 'Very Good', 'Excellent'];
            for (let i: number = 0; i < li.length; ++i) {
                (li[i].querySelectorAll('.e-tick-both')[1] as HTMLElement).innerText = remarks[i];
            }
        }
    });
    customTicks.appendTo('#slider');
```

{% endtab %}