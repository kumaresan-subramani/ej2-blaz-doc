---
title: "Syncfusion JavaScripr Range Slider Formatting"
component: "Slider"
description: "Learn about JavaScript range slider control formatting, to customize slider values like time, currency and kilometer, values also displayed in ticks & tooltip."
---

# Formatting

The `format` feature used to customize the units of Slider values to desired format. The formatted values will also be applied to the ARIA attributes of the slider. There are two ways of achieving formatting in slider.

* Use the [format](../api/slider/tooltipData#format) API of slider which utilizes our [Internationalization](../common/internationalization/) to format values.

* Customize using the events namely `renderingTicks` and `tooltipChange`.

{% tab template="slider/format", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="format-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let sliderObj: Slider = new Slider({
    min: 0, max: 100, step: 1, value: 30,
    // Applying currency formatting for tooltip with two decimal specifiers
    tooltip: { isVisible: true, format: 'C2' },
    // Applying currency formatting for ticks with two decimal specifiers
    ticks: { placement: 'After', format: 'C2', largeStep: 20, smallStep: 10, showSmallTicks: true }
});
// Render initialized Slider
sliderObj.appendTo('#slider');

```

{% endtab %}

## Using format API

In this method, we have different predefined formatting styles like Numeric (N), Percentage (P), Currency (C) and `#` specifiers. In this below example we have formatted the `ticks` and `tooltip` values into percentage.

{% tab template="slider/format-api", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="api-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let percentObj: Slider = new Slider({
    min: 0, max: 1, value: .3, step: .01,
    // Assigning ticks values to percentage formatting
    ticks: { placement: 'After', largeStep: .2, smallStep: .1, showSmallTicks: true, format: 'P0' },
    // Assigning tooltip values to percentage formatting
    tooltip: { placement: 'Before', isVisible: true, showOn: 'Always', format: 'P0' },
});
// Render initialized Slider
percentObj.appendTo('#slider');

```

{% endtab %}

## Using Events

In this method, we will be retrieving the values from the slider events then process them to desired formatted the values.
In this sample we have customized the `ticks` values into weekdays as one formatting and `tooltip` values into day of the week as another formatting.

{% tab template="slider/events", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="event-template" %}

```typescript

import { Slider, SliderTickEventArgs, SliderTooltipEventArgs } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let eventObj: Slider = new Slider({
        // Minimum value
        min: 0,
        // Maximum value
        max: 6,
        // Slider current value
        value: 2,
        // Assigning ticks data
        ticks: {
            placement: 'After',
            largeStep: 1
        },
        renderingTicks: function (args: SliderTickEventArgs) {
                // Weekdays Array
                let daysArr: string [] = ['Sunday','Monday','Tuesday','Wednesday','Thrusday','Friday','Saturday'];
                // Customizing each ticks text into weeksdays
                args.text = daysArr[parseFloat(args.value as any)];
        },
        tooltipChange: function (args: SliderTooltipEventArgs) {
                // Customizing tooltip to display the Day (in numeric) of the week
                args.text =  'Day ' + (Number(args.value) + 1).toString();
        },
        // Assigning tooltip data
        tooltip: {
            placement: 'Before',
            isVisible: true
        }
    });
    // Render initialized Slider
    eventObj.appendTo('#slider');

```

{% endtab %}
