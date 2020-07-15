---
title: "Syncfusion JavaScript Range Slider Ticks"
component: "Slider"
description: "Learn about JavaScript range slider's visual representation of values using ticks with small and large ticks, which is placed before, after or both sides of slider bar."
---

# Ticks

The Ticks in Slider supports you to easily identify the current value/values of the Slider. It contains `smallStep` and `largeStep`. The value of the major ticks alone
will be displayed in the slider. In order to enable/disable the small ticks, use the `showSmallTicks` property.

{% tab template="slider/ticks", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css" es5Template="ticks-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let sliderObj: Slider = new Slider({
        tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        value: 30,
        // Slider ticks customization
        ticks: { placement: 'After', largeStep: 20, smallStep: 10, showSmallTicks: true }
    });
    // Render initialized Slider
    sliderObj.appendTo('#slider');

```

{% endtab %}

## Step

When the Slider is moved, it increases/decreases the value
based on the step value. By default, the value is increased/decreased by 1. Use the `step` property to change the increment step value.

{% tab template="slider/step", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="step-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let rangeObj: Slider = new Slider({
        ticks: { placement: 'After', largeStep: 20, smallStep: 10, showSmallTicks: true },
        tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        value: 30,
        // Enables step
        step: 10
    });
    // Render initialized Slider
    rangeObj.appendTo('#slider');

```

{% endtab %}

## Min and Max

Enables the minimum/starting and maximum/ending value of the Slider, by using the `min` and `max`
property. By default, the minimum value is 1 and maximum value is 100. In the following sample the slider is rendered with the min value as 100 and max value as 1000.

{% tab template="slider/min-max", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="min-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let rangeObj: Slider = new Slider({
        ticks: { placement: 'After', largeStep: 200, smallStep: 100, showSmallTicks: true },
        tooltip: { placement: 'Before', isVisible: true, showOn: 'Always' },
        // Minimum value
        min: 100,
        // Maximum value
        max: 1100,
        // Slider current value
        value: 400
    });
    // Render initialized Slider
    rangeObj.appendTo('#slider');

```

{% endtab %}