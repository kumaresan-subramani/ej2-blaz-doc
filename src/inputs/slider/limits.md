---
title: "Syncfusion JavaScript Range Slider Limits"
component: "Slider"
description: "Learn about JavaScript range slider control limits feature to restrict thumb movement in min and max values and also supports interval dragging between range values."
---

# Movement Limits and Drag Interval

The slider limits restrict the slider thumb between a particular range. This is used if higher or lower value affects the process
or product where the slider is being used.

The following are the six options in the slider's limits object. Each API in the limits object is optional.

* ``enabled``: Enables the limits in the Slider.
* ``minStart``: Sets the minimum limit for the first handle.
* ``minEnd``: Sets the maximum limit for the first handle.
* ``maxStart``: Sets the minimum limit for the second handle.
* ``maxEnd``: Sets the maximum limit for the second handle.
* ``startHandleFixed``: Locks the first handle.
* ``endHandleFixed``: Locks the second handle.

## Default and MinRange Slider limits

There is only one handle in the Default and MinRange Slider, so ``minStart``, ``minEnd``, and ``startHandleFixed`` options can be used.
When the limits are enabled in the Slider, the limited area becomes darken. So you can differentiate the allowed and restricted area.
Refer to the following snippet to enable the limits in the Slider.

```typescript

let slider = new Slider({
    ......

    limits: { enabled: true, minStart: 10, minEnd: 40 }

    ......
});

```

{% tab template="slider/default-limit", sourceFiles="app.ts,index.html,index.css", isDefaultActive=true, es5Template="default-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialization of Slider
let slider: Slider = new Slider({
    min: 0,
    max: 100,
    value: 30,
    type: 'MinRange',
    limits: { enabled: true, minStart: 10, minEnd: 40 },
    tootip: { isVisible: true }
});
// Render initialized Slider
slider.appendTo('#slider');

```

{% endtab %}

## Range Slider limits

In the range slider, both handles can be restricted and locked from the limit's object. In this sample, the first handle is limited between
10 and 40, and the second handle is limited between 60 and 90.

```typescript

let slider = new Slider({
    ......

    limits: { enabled: true, minStart: 10, minEnd: 40, maxStart: 60, maxEnd: 90 }

    ......
});

```

{% tab template="slider/range-limit",sourceFiles="app.ts,index.html,index.css",isDefaultActive=true, es5Template="range-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialization of Slider
let slider: Slider = new Slider({
    min: 0,
    max: 100,
    type: 'Range',
    value: [30, 70],
    limits: { enabled: true, minStart: 10, minEnd: 40, maxStart: 60, maxEnd: 90 },
    tootip: { isVisible: true }
});
// Render initialized Slider
slider.appendTo('#slider');

```

{% endtab %}

## Handle lock

The movement of slider handles can be locked by enabling the ``startHandleFixed`` and ``endHandleFixed`` properties in the limit's object.
In this sample, the movement of both slider handles has been locked.

```typescript

let slider = new Slider({
    ......

    limits: { enabled: true, startHandleFixed: true, endHandleFixed: true }

    ......
});

```

{% tab template="slider/handle-lock",sourceFiles="app.ts,index.html,index.css",isDefaultActive=true, es5Template="lock-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialization of Slider
let slider: Slider = new Slider({
    min: 0,
    max: 100,
    type: 'Range',
    value: [30, 70],
    limits: { enabled: true, startHandleFixed: true, endHandleFixed: true },
    tooltip: { isVisible: true }
});
// Render initialized Slider
slider.appendTo('#slider');

```

{% endtab %}