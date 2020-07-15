# Customize the bar

Slider appearance can be customized through CSS. By overriding the slider CSS classes, you can customize the slider bar. The slider bar can be customized with different themes. By default, slider have class name `e-slider-track` for bar. The class can be overridden with our own color values like the following code snippet.

```css
.e-control.e-slider .e-slider-track .e-range {
           background: linear-gradient(left, #e1451d 0, #fdff47 17%, #86f9fe 50%, #2900f8 65%, #6e00f8 74%, #e33df9 83%, #e14423 100%);
}
```

You can also apply background color for a certain range depending upon slider values, using change event.

```typescript
change: (args: SliderChangeEventArgs) => {
        if (args.value > 0 && args.value <= 25) {
            // Change handle and range bar color to green when
            (sliderHandle as HTMLElement).style.backgroundColor = 'green';
            (sliderTrack as HTMLElement).style.backgroundColor = 'green';
        } else if (args.value > 25 && args.value <= 50) {
            // Change handle and range bar color to royal blue
            (sliderHandle as HTMLElement).style.backgroundColor = 'royalblue';
            (sliderTrack as HTMLElement).style.backgroundColor = 'royalblue';
        } else if (args.value > 50 && args.value <= 75) {
            // Change handle and range bar color to dark orange
            (sliderHandle as HTMLElement).style.backgroundColor = 'darkorange';
            (sliderTrack as HTMLElement).style.backgroundColor = 'darkorange';
        } else if (args.value > 75 && args.value <= 100) {
            // Change handle and range bar color to red
            (sliderHandle as HTMLElement).style.backgroundColor = 'red';
            (sliderTrack as HTMLElement).style.backgroundColor = 'red';
        }
    }
```

{% tab template="slider/bar-customization", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="bar-customization" %}

```typescript

import { Slider, SliderChangeEventArgs } from '@syncfusion/ej2-inputs';

    // Initialize Slider component
    let heightSlider: Slider = new Slider({
        // Set the value for slider
        value: 30,
        min: 0, max: 100
    });
    heightSlider.appendTo('#height_slider');

    // Initialize Slider component
    let gradientSlider: Slider = new Slider({
        // Set slider minimum and maximum values
        min: 0, max: 100,
        // Set the intial range values for slider
        value: 50,
        type: 'MinRange'
    });
    gradientSlider.appendTo('#gradient_slider');

    let sliderTrack: HTMLElement;
    let sliderHandle: HTMLElement;

    // Initialize Slider component
    let dynamicColorSlider: Slider = new Slider({
        // Set slider minimum and maximum values
        min: 0, max: 100,
        value: 20,
        type: 'MinRange',
        // Handler used for slider created event
        created: () => {
            sliderTrack = (document.getElementById('dynamic_color_slider') as HTMLElement).querySelector('.e-range');
            sliderHandle = (document.getElementById('dynamic_color_slider') as HTMLElement).querySelector('.e-handle');
            (sliderHandle as HTMLElement).style.backgroundColor = 'green';
            (sliderTrack as HTMLElement).style.backgroundColor = 'green';
        },
        // Handler used for slider change event
        change: (args: SliderChangeEventArgs) => {
            if (args.value > 0 && args.value <= 25) {
                // Change handle and range bar color to green when
                (sliderHandle as HTMLElement).style.backgroundColor = 'green';
                (sliderTrack as HTMLElement).style.backgroundColor = 'green';
            } else if (args.value > 25 && args.value <= 50) {
                // Change handle and range bar color to royal blue
                (sliderHandle as HTMLElement).style.backgroundColor = 'royalblue';
                (sliderTrack as HTMLElement).style.backgroundColor = 'royalblue';
            } else if (args.value > 50 && args.value <= 75) {
                // Change handle and range bar color to dark orange
                (sliderHandle as HTMLElement).style.backgroundColor = 'darkorange';
                (sliderTrack as HTMLElement).style.backgroundColor = 'darkorange';
            } else if (args.value > 75 && args.value <= 100) {
                // Change handle and range bar color to red
                (sliderHandle as HTMLElement).style.backgroundColor = 'red';
                (sliderTrack as HTMLElement).style.backgroundColor = 'red';
            }
        }
    });
    dynamicColorSlider.appendTo('#dynamic_color_slider');
```

{% endtab %}