---
title: "Getting Started"
component: "DatePicker"
description: "This getting started section briefly explains how to create a date picker component in an application."
---

# Getting Started

This section briefly explains how to create a simple DatePicker
component and configure its available functionalities in TypeScript, using Essential JS 2
[quickstart](https://github.com/syncfusion/ej2-quickstart)
 seed repository.

## Dependencies

The following list of dependencies is required to use DatePicker component in your application.

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

To get you started with DatePicker component, you can clone the
[Essential JS 2 quickstart](https://github.com/syncfusion/ej2-quickstart.git) application and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [application](https://github.com/syncfusion/ej2-quickstart.git)
is configured with all the EJ2 dependencies. For better understanding, remove common
settings (`src/styles/styles.css`, `system.config.js` ) to
get started with the DatePicker component.

* Refer to the [DatePicker component dependencies](./getting-started#dependencies) in `system.config.js` configuration file.

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
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});

System.import('app');
```

## Adding Style sheet to the Application

To render the DatePicker component, need to import DatePicker and its dependent component's styles as given below in `style.css`.

```css
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
```

> If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Add DatePicker to the application

Add the HTML input element for DatePicker into your `index.html` file.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 DatePicker component</title>
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
        <!--element which is going to render the DatePicker-->
        <input id="element"/>
    </div>

</body>

</html>
```

Now import the  DatePicker component into your `app.ts` and append it to `#element`
`[src/app/app.ts]`

```typescript

import { DatePicker } from '@syncfusion/ej2-calendars';

// initialize datepicker component
let datepickerObject: DatePicker = new DatePicker();
// render initialized datepicker
datepickerObject.appendTo('#element');

```

## Run the application

Now use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The below example shows a basic DatePicker.

{% tab template="datepicker/getting-started",sourceFiles="app.ts,index.html", es5Template="datepicker-basic-template" %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
// creates a simple datepicker component
let datepickerObject: DatePicker = new DatePicker({
    // sets the placeholder
    placeholder: 'Enter date'
});
datepickerObject.appendTo('#element');
```

{% endtab %}

## Setting the value, min and max dates

The following example demonstrates how to set the value, min and max dates on initializing the
DatePicker. Here you can able to select a date within a range from 9th to 15th.

{% tab template="datepicker/getting-started", sourceFiles="app.ts,index.html",es5Template="datepicker-minmax-template" %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';

let month: number = new Date().getMonth();
let fullYear: number = new Date().getFullYear();
// creates a datepicker with min max property
let datepickerObject: DatePicker = new DatePicker({
    // Sets the min.
    min: new Date(fullYear, month , 9),
    //Sets the max.
    max: new Date(fullYear, month, 15),
    // Sets the value.
    value: new Date(fullYear, month , 11)
});
datepickerObject.appendTo('#element');
```

{% endtab %}

## See Also

* [Change the format of selected date](./date-format)
* [Render DatePicker with specific culture](./globalization)
* [How to change the initial view of the DatePicker](./date-views)
* [How to achieve validation with DatePicker](./how-to/client-side-validation)
