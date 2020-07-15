---
title: "Slider Getting Started"
component: "Slider"
description: "Getting started with typescript Slider control."
---

# Getting Started

The following section explains the required steps to build the Slider control with its basic
usage in step-by-step procedure.

## Dependencies

The following list of dependencies are required to use the Slider control in your application.

```javascript

|-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-buttons

```

## Set up your development environment

To get started with Slider control, you can clone the
[Essential JS 2 quickstart](https://github.com/syncfusion/ej2-quickstart.git) project, and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with the common
settings (`src/styles/styles.css`, `system.config.js`) to start
with all Essential JS 2 controls.

## Adding Slider to the project

Add the div element with the id attribute `#slider` inside the body tag in your `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 Slider control</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="shortcut icon" href="resources/favicon.ico" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <div>
        <div class='wrap'>
            <!--element which is going to render the Slider -->
             <div id="slider"></div>
        </div>
    </div>
</body>

<style>
.wrap {
  height: 260px;
  margin: 0 auto;
  padding: 30px 10px;
  width: 260px;
}
</style>

</html>

```

Import the  Slider control into your `app.ts` and append it to `#slider`
`[src/app/app.ts]`

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialization of Slider control
let slider: Slider = new Slider();

// Render initialized Slider
slider.appendTo('#slider');

```

## Run the application

The `Essential JS 2 quickstart` application project is configured to compile and run the application in browser.
Use the following command to run the application.

```shell
npm start
```

{% tab template="slider/getting-started", sourceFiles="app.ts,index.html", isDefaultActive=true %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialization of Slider
let slider: Slider = new Slider({value: 30});
// Render initialized Slider
slider.appendTo('#slider');

```

{% endtab %}

## Types

The types of Slider are as follows:

| **Types** | **Usage** |
| --- | --- |
| Default | Shows a default Slider to select a single value. |
| MinRange | Displays the shadow from the start value to the current selected value. |
| Range | Selects a range of values. It also displays the shadow in-between the selection range. |

>Both the Default Slider and Min-Range Slider have same behavior that is used to select a single value.
In Min-Range Slider, a shadow is considered from the start value to current handle position. But the Range Slider
contains two handles that is used to select a range of values and a shadow is considered in between the two handles.

{% tab template="slider/types", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css" %}

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

## Customization

### Orientation

The Slider can be displayed, either in horizontal or vertical orientation. By default, the Slider renders in horizontal orientation.

{% tab template="slider/getting-started",  isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css" %}

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

### Tooltip

The Slider displays the tooltip to indicate the current value by clicking the Slider bar or drag
the Slider handle. The Tooltip position can be customized by using the `placement` property. Also decides the tooltip display mode on a page, i.e., on hovering, focusing, or clicking on the Slider handle and it always remains/displays on the page.

{% tab template="slider/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css" %}

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

### Buttons

The Slider value can be changed by using the Increase and Decrease buttons. In Range Slider, by
default the first handle value will be changed while clicking the button. Change the handle focus and
press the button to change the last focused handle value.

> After enabling the slider buttons if the 'Tab' key is pressed, the focus goes to the handle
and not to the button.

{% tab template="slider/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css" %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialize Slider control
 let rangeObj: Slider = new Slider({
        // Enable the button option in Slider
        showButtons: true,
        value: [30, 70],
        type: 'Range'
    });
    // Render initialized Slider
    rangeObj.appendTo('#slider');

```

{% endtab %}