---
title: "Syncfusion JavaScript Slider Types"
component: "Slider"
description: "This section helps to lean about different types of JavaScript sliders, such as default, min range and range."
---

# Types

The types of Slider are as follows:

| **Types** | **Usage** |
| --- | --- |
| Default | Shows a default Slider to select a single value. |
| MinRange | Displays the shadow from the start value to the current selected value. |
| Range | Selects a range of values. It also displays the shadow in-between the selection range. |

>Both the Default Slider and Min-Range Slider have same behavior that is used to select a single value.
In Min-Range Slider, a shadow is considered from the start value to current handle position. But the Range Slider
contains two handles that is used to select a range of values and a shadow is considered in between the two handles.

{% tab template="slider/types", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="types-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize default Slider control
 let defaultObj: Slider = new Slider({
        value: 30
    });
    defaultObj.appendTo('#default');

    // Initialize minrange Slider control
    let minRangeObj: Slider = new Slider({
        value: 30,
        type: 'MinRange'
    });
    minRangeObj.appendTo('#minrange');

    // Initialize range Slider control
    let rangeObj: Slider = new Slider({
        value: [30, 70],
        type: 'Range'
    });
    rangeObj.appendTo('#range');

```

{% endtab %}