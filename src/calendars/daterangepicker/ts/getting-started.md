---
title: "Getting Started"
component: "DateRangePicker"
description: "This getting started section briefly explains how to create a date range picker component in an application."
---

# Getting Started

This section briefly explains about how to create and configure a simple DateRangePicker
component.

## Dependencies

The following list of dependencies are required to use DateRangePicker component in your application.

```javascript
|-- @syncfusion/ej2-calendars
  |-- @syncfusion/ej2-base
  |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-splitbuttons
  |-- @syncfusion/ej2-lists
  |-- @syncfusion/ej2-data
  |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-buttons
```

## Set up your development environment

To start the DateRangePicker component, clone the
[Essential JS 2 quickstart](https://github.com/syncfusion/ej2-quickstart.git) application, and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [application](https://github.com/syncfusion/ej2-quickstart.git)
is preconfigured with all the EJ2 dependencies. For better understanding, remove common
settings (`src/styles/styles.css`, `system.config.js` ) to
get started with the DateRangePicker component.

* Refer to the [DateRangePicker component dependencies](./getting-started#dependencies) in `system.config.js` configuration file.

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

To render the DateRangePicker component, need to import DateRangePicker and its dependent component's styles as given below in `style.css`.

```css
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
```

> If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Add DateRangePicker to the application

Add the HTML input element with an ID attribute as element for DateRangePicker to your `index.html` file.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 DateRangePicker component</title>
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
    <div style="margin: 50px;">
        <!--element which is going to render the DateRangePicker-->
        <input id="element"/>
    </div>

</body>

</html>
```

Import the  DateRangePicker component to your `app.ts` and append it to the `#element`
`[src/app/app.ts]`.

```typescript

import { DateRangePicker } from '@syncfusion/ej2-calendars';

// initialize daterangepicker component
let daterangepicker: DateRangePicker = new DateRangePicker();
daterangepicker.appendTo('#element');

```

## Run the application

Use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The following example shows a basic DateRangePicker.

{% tab template="daterangepicker/getting-started",sourceFiles="app.ts,index.html",
es5Template="daterangepicker-basic-template"%}

```typescript
import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates a simple daterangepicker component
let daterangepicker: DateRangePicker = new DateRangePicker({
//sets the place holder
placeholder:"Select Range"
});
daterangepicker.appendTo('#element');

```

{% endtab %}

## Setting the start and end date

The start and end date in a range can be defined with the help of startDate and endDate property.
The following example demonstrates to set the start and end date on initializing the
DateRangePicker.

{% tab template="daterangepicker/getting-started", sourceFiles="app.ts,index.html",
es5Template="daterangepicker-minmax-template" %}

```typescript
import { DateRangePicker } from '@syncfusion/ej2-calendars';
// creates a daterangepicker with start and end date
let daterangepicker: DateRangePicker = new DateRangePicker({
//sets the start date in the range
startDate: new Date("11/9/2017"),
//sets the end date in the range
endDate: new Date("11/21/2017")
});
daterangepicker.appendTo('#element');
```

{% endtab %}

## See Also

* [Render DateRangePicker with pre-defined ranges](./customization#preset-ranges)
* [Render DateRangePicker with specific culture](./globalization)
