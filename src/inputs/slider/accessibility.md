---
title: "Syncfusion JavaScript Range Slider Accessibility"
component: "Slider"
description: "Learn JavaScript range slider control WAI-ARIA & WGCA accessibility standards, that helps to access slider via keyboard on-screen readers or assistive technology devices"
---

# Accessibility

The Slider is characterized with complete ARIA Accessibility support that helps to access
by on-screen readers and other assistive technology devices. This control is designed with the
reference of guidelines document given in the [WAI ARAI Accessibility Practices](https://www.w3.org/TR/wai-aria-practices/#slider).

The Slider control uses the `Slider` role and the following ARIA properties for its element based on the state.

| **Property** | **Functionalities** |
| --- | --- |
| aria-valuenow | It Indicates the current value of the slider. |
| aria-valuetext | Returns the current text of the slider. |
| aria-valuemin | It Indicates the Minimum value of the slider. |
| aria-valuemax | It Indicates the Maximum value of the slider. |
| aria-orientation | It Indicates the Slider Orientation. |
| aria-label | Slider left and right button label text (increment and decrement). |
| aria-labelledby | It indicates the name of the Slider. |

## Keyboard interaction

The Keyboard interaction of the Slider control is designed based on the
[WAI-ARIA Practices](https://www.w3.org/TR/wai-aria-practices/#slider ) described for Slider.
Users can use the following shortcut keys to interact with the Slider.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Right Arrow</kbd>&nbsp;&nbsp; &#124;&nbsp;&nbsp; <kbd>Up Arrow</kbd></td><td>
Increase the Slider value.
</td></tr>
<tr>
<td>
<kbd>Left Arrow</kbd>&nbsp;&nbsp; &#124;&nbsp;&nbsp; <kbd>Down Arrow</kbd></td><td>
Decrease the Slider value.</td></tr>
<tr>
<td>
<kbd>Home</kbd></td><td>
Moves to the start value (for Range Slider when the second thumb is focused and the Home key is pressed, it moves to the first thumb value).</td></tr>
<tr>
<td>
<kbd>End</kbd></td><td>
Moves to the end value (for Range Slider when the first thumb is focused and the End key is pressed, it moves to the second thumb value).</td></tr>
<tr>
<td>
<kbd>Page Up</kbd></td><td>
Increases the Slider by `largeStep` value.</td></tr>
<tr>
<td>
<kbd>Page Down</kbd></td><td>
Decreases the Slider by `largeStep` value.</td></tr>
</table>

{% tab template="slider/accessibility", sourceFiles="app.ts,index.html,index.css", isDefaultActive=true, es5Template="access-template" %}

```typescript

import { Slider, SliderTooltipEventArgs, SliderTickEventArgs } from "@syncfusion/ej2-inputs";

// Initialize Slider component
let minRangeObj: Slider = new Slider({
  ticks: {
    placement: "After",
    largeStep: 20,
    smallStep: 10,
    showSmallTicks: true
  },
  tooltip: { placement: "Before", isVisible: true, showOn: "Always" },
  value: 30,
  step: 10,
  type: "MinRange",
  showButtons: true
});
// Render initialized Slider
minRangeObj.appendTo("#slider");

let weekdaysObj: Slider = new Slider({
  min: 0,
  max: 6,
  step: 1,
  value: 2,
  // Assigning ticks data
  ticks: {
    placement: "After",
    largeStep: 1
  },
  renderingTicks: function(args: SliderTickEventArgs) {
    // Weekdays Array
    let daysArr: string[] = [
      "Sunday",
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thrusday",
      "Friday",
      "Saturday"
    ];
    // Customizing each ticks text into weeksdays
    args.value = daysArr[parseFloat(args.value as any).toString()];
  },
  // Assigning tooltip data
  tooltip: {
    placement: "Before",
    isVisible: true
  },
  tooltipChange: function(args: SliderTooltipEventArgs) {
    // Customizing tooltip to display the Day (in numeric) of the week
    args.text = "Day " + (Number(args.text) + 1).toString();
  }
});
// Render initialized Slider
weekdaysObj.appendTo("#slider1");

```

{% endtab %}