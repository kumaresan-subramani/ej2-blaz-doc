# Customize the thumb

Slider appearance can be customized through CSS. By overriding the slider CSS classes, you can customize the thumb. By default, slider has unique class `e-handle` for slider thumb. You can override the following class as per your requirement. Here, in the sample, the slider thumb has been customized to square, circle, oval shapes, and background image has also been customized.

```typescript
.e-control.e-slider .e-handle {
    background-image: url('https://ej2.syncfusion.com/demos/src/slider/images/thumb.png');
    background-color: transparent;
    height: 25px;
    width: 25px;
}
#square_slider.e-control.e-slider .e-handle {
    border-radius: 0%;
    background-color: #f9920b;
    border: 0;
}
#circle_slider.e-control.e-slider .e-handle {
    border-radius: 50%;
    background-color: #f9920b;
    border: 0;
}
#oval_slider.e-control.e-slider .e-handle {
    height: 25px;
    width: 8px;
    top: 3px;
    border-radius: 15px;
    background-color: #f9920b;
}
```

{% tab template="slider/thumb-customization", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="thumb-customization" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { Slider } from '@syncfusion/ej2-inputs';

    // Initialize slider control
    let squareSlider: Slider = new Slider({
        // Set the value for slider
        value: 30,
        min: 0, max: 100
    });
    squareSlider.appendTo('#square_slider');

    // Initialize slider control
    let circleSlider: Slider = new Slider({
        // Set the value for slider
        value: 30,
        // Set slider minimum and maximum values
        min: 0, max: 100
    });
    circleSlider.appendTo('#circle_slider');

    // Initialize slider control
    let ovalSlider: Slider = new Slider({
        // Set the value for slider
        value: 30,
        // Set slider minimum and maximum values
        min: 0, max: 100
    });
    ovalSlider.appendTo('#oval_slider');

    // Initialize slider control
    let imageSlider: Slider = new Slider({
        // Set the value for slider
        value: 30,
        // Set slider minimum and maximum values
        min: 0, max: 100,

        ticks: { placement: 'After' }

    });
    imageSlider.appendTo('#image_slider');
```

{% endtab %}