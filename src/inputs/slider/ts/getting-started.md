---
title: "Syncfusion JavaScript Range Slider Getting Started"
component: "Slider"
description: "This section helps to learn how to create the JavaScript range slider control with its basic usage in step-by-step procedure."
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

## Adding CSS reference

Combined CSS files are available in the Essential JS 2 package root folder. This can be referenced in your `[src/styles/styles.css]` using the following code.

```css
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
```

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

{% tab template="slider/getting-started", sourceFiles="app.ts,index.html,index.css" isDefaultActive=true %}

```typescript

import { Slider } from '@syncfusion/ej2-inputs';

// Initialization of Slider
let slider: Slider = new Slider({value: 30});
// Render initialized Slider
slider.appendTo('#slider');

```

{% endtab %}

## See Also

[Slider Types](./types/)

[Slider Formatting](./format/)

[Orientation Slider](./orientation/)

[Ticks in Slider](./ticks/)

[Tooltip in Slider](./tooltip/)