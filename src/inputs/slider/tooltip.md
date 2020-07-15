---
title: "Syncfusion JavaScript Range Slider Tooltip"
component: "Slider"
description: "This section helps to learn how to display currently selected value of JavaScript range slider using tooltip, which is displayed before or after of slider bar."
---

# Tooltip

The Slider displays the tooltip to indicate the current value by clicking the Slider bar or drag
the Slider handle. The Tooltip position can be customized by using the `placement` property. Also decides the tooltip display mode on a page, i.e., on hovering, focusing, or clicking on the Slider handle and it always remains/displays on the page.

{% tab template="slider/tooltip", isDefaultActive = "true", sourceFiles="app.ts, index.html", es5Template="tooltip-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let rangeObj: Slider = new Slider({
        // Slider tooltip
        tooltip: { placement: 'After', isVisible: true, showOn: 'Always' },
        value: 30,
        type: 'MinRange'
    });
    // Render initialized Slider
    rangeObj.appendTo('#slider');

```

{% endtab %}

## Buttons

The Slider value can be changed by using the Increase and Decrease buttons. In Range Slider, by
default the first handle value will be changed while clicking the button. Change the handle focus and
press the button to change the last focused handle value.

> After enabling the slider buttons if the 'Tab' key is pressed, the focus goes to the handle
and not to the button.

{% tab template="slider/buttons", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="buttons-template" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let rangeObj: Slider = new Slider({
        // Slider tooltip
        tooltip: { placement: 'After', isVisible: true, showOn: 'Always' },
        value: 30,
        type: 'MinRange'
        showButtons: true
    });
    // Render initialized Slider
    rangeObj.appendTo('#slider');

```

{% endtab %}