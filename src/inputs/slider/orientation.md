---
title: "Syncfusion JavaScript Range Slider Orientation"
component: "Slider"
description: "This section helps to learn how to initialize JavaScript range slider control in horizontal and vertical orientation along with tooltip and ticks."
---

# Orientation

The Slider can be displayed, either in horizontal or vertical orientation. By default, the Slider renders in horizontal orientation.

{% tab template="slider/orientation", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="orientation-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let rangeObj: Slider = new Slider({
        // vertical orientation
        orientation: 'Vertical',
        value: 30
    });
    // Render initialized Slider
    rangeObj.appendTo('#slider');

```

{% endtab %}
