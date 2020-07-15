---
title: "Getting Started"
component: "TimePicker"
description: "This getting started section briefly explains how to create a time picker component in an application."
---

# Getting Started

This section briefly explains how to create a simple **TimePicker** component, and configure its available functionalities in TypeScript
using Essential JS 2 [quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.

## Dependencies

Install the below required dependency package in order to use the `TimePicker` component in your application.

```javascript
|-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-inputs
        |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-buttons
```

## Set up your development environment

To get started with TimePicker component, you can clone the
[`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) application, and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The project is preconfigured with common settings (`src/styles/styles.css`, `system.config.js` ) to start all Essential JS 2 components.

* Refer to the [TimePicker component dependencies](./getting-started#dependencies) in `system.config.js` configuration file.

`[src/system.config.js]`

```js
System.config({
    paths: {
        'npm:': './node_modules/',
        'syncfusion:': 'npm:@syncfusion/'
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});

System.import('app');
```

## Adding Style sheet to the Application

To render the TimePicker component, need to import TimePicker and its dependent component's styles as given below in `style.css`.

```css
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
```

> If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Add TimePicker to the application

Add the HTML input element for TimePicker to your `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 TimePicker component</title>
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
    <div style="margin: 20px 0px; width:250px">
        <!--element to render the TimePicker-->
        <input id="element"/>
    </div>

</body>

</html>
```

Import the  TimePicker component into your `app.ts` and append it to the `#element`
`[src/app/app.ts]`.

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);

// initialize timepicker component
let timeObject: TimePicker = new TimePicker({
    placeholder: 'Select a Time'
});

// render initialized timepicker
timeObject.appendTo('#element');

```

## Run the application

Use the following command to run the application in the browser.

```cmd
npm run start
```

The following example shows a basic TimePicker.

{% tab template="timepicker/getting-started",sourceFiles="app.ts,index.html",
es5Template="timepicker-basic-template" %}

```typescript
import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);

// creates the simple timepicker component
let timeObject: TimePicker = new TimePicker({
    placeholder: 'Select a Time'
});
timeObject.appendTo('#element');
```

{% endtab %}

Now, the TimePicker renders with  default culture as `American English`('en-US'). For a different culture, refer to the
[`Globalization`](../timepicker/globalization/) section.

## Setting the value, min, and max time

The following example demonstrates how to set the value, min, and max time on initializing
the TimePicker. The TimePicker allows you to select the time value within a range from `7:00 AM` to `4:00 PM`.

{% tab template="timepicker/getting-started" , sourceFiles="app.ts,index.html",
es5Template="timepicker-minmax-template" %}

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);

let month: number = new Date().getMonth();
let fullYear: number = new Date().getFullYear();
let date: number = new Date().getDate();

// creates timepicker with min max property
let timeObject: TimePicker = new TimePicker({
    // Sets the min.
    min: new Date(fullYear, month , date,7),
    //Sets the max.
    max: new Date(fullYear, month, date, 16),
    // Sets the value.
    value: new Date(fullYear, month , date, 13)
});
timeObject.appendTo('#element');

```

{% endtab %}

## Setting the time format

Time formats is a way of representing the time value in different string format in textbox and popup
list. By default, the TimePicker's format is based on the culture. You can also customize the format by using the
[`format`](../../api/timepicker#format)
property. To know more about the time format standards, refer to the
[Date and Time Format](../../common/internationalization#custom-formats) section.

The following example demonstrates the TimePicker component in 24 hours format with 60 minutes
interval. The time interval is set to
60 minutes by using the [`step`](../../api/timepicker#step) property.

{% tab template="timepicker/getting-started", sourceFiles="app.ts,index.html",
es5Template="timepicker-timeformat-template"%}

```typescript

import { TimePicker } from '@syncfusion/ej2-calendars';
import { enableRipple } from '@syncfusion/ej2-base';

//enable ripple style
enableRipple(true);

// creates the simple timepicker component
let timeObject: TimePicker = new TimePicker({
    value: new Date(),
    // sets the format property to display the time value in 24 hours format.
    format: 'HH:mm',
    // specify the interval value.
    step: 60,
});
timeObject.appendTo('#element');

```

{% endtab %}

> Once the time format property is defined, it will be applicable to all the cultures.

## See Also

* [Render TimePicker with min and max time](./time-range)
* [How to achieve validation with TimePicker](./how-to/client-side-validation-using-form-validator)
* [Render TimePicker with specific culture](./globalization)