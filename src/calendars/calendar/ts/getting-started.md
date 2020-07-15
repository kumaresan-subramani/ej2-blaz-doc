---
title: "Getting Started"
component: "Calendar"
description: "This getting started section briefly explains how to create a calendar component in an application."
---

# Getting Started

This section explains how to create a simple Calendar and how to configure the Calendar component.

## Dependencies

The list of dependencies required to use the Calendar component in your application is given below:

```javascript
|-- @syncfusion/ej2-calendars
  |-- @syncfusion/ej2-base
  |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-splitbuttons
  |-- @syncfusion/ej2-lists
  |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-buttons
```

## Set up your development environment

To start the Calendar component, clone the [`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) application, and install the packages using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [application](https://github.com/syncfusion/ej2-quickstart.git)
is preconfigured with common settings (`src/styles/styles.css, src/system.config.js` ) to start all Essential JS 2 components.

* Refer to the [Calendar component dependencies](./getting-started#dependencies) in `system.config.js` configuration file.

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

To render Calendar component, need to import Calendar and its dependent components styles as given below in `style.css`.

```css
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
```

> If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

## Add Calendar to the application

Add the HTML div tag with an ID attribute as the `element` to your `index.html` file.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 Calendar component</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="shortcut icon" href="resources/favicon.ico" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />

    <!--Style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--System js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <div style="margin: 50px;">
        <!--Element which is going to render the Calendar-->
        <div id="element"></div>
    </div>

</body>

</html>
```

Then, import the Calendar component to your `app.ts` file, and initialize it with the `#element`
`[src/app/app.ts]`.

```typescript
import { Calendar } from '@syncfusion/ej2-calendars';
//Initialize calendar component.
let calendarObject: Calendar = new Calendar();
//Render initialized calendar.
calendarObject.appendTo('#element');
```

## Run the application

Now, run the application by using the command below.

```cmd
npm run start
```

The following example shows a basic Calendar component.

{% tab template="calendar/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css" ,es5Template="calendar-basic-template" %}

```typescript
import { Calendar, ChangedEventArgs } from '@syncfusion/ej2-calendars';
// Creates a simple calendar component.
let calendarObject: Calendar = new Calendar();
calendarObject.appendTo('#element');
```

{% endtab %}

## Setting the value, min and max dates

After rendering a simple Calendar component by following the above steps, configure the Calendar to set a value within a specific range using its value, min, and max properties.

Here the Calendar allows you to select a date within the range from 9th to 15th.

{% tab template="calendar/getting-started", sourceFiles="app.ts,index.html,styles.css",es5Template="calendar-minmax-template" %}

```typescript
import { Calendar, ChangedEventArgs } from '@syncfusion/ej2-calendars';

let month: number = new Date().getMonth();
let fullYear: number = new Date().getFullYear();
// Creates a calendar with min max property.
let calendarObject: Calendar = new Calendar({
    // Sets the min.
    min: new Date(fullYear, month , 9),
    //Sets the max.
    max: new Date(fullYear, month, 15),
    // Sets the value.
    value: new Date(fullYear, month , 11)
});
calendarObject.appendTo('#element');
```

{% endtab %}

## See Also

* [Select multiple dates in the Calendar](./multi-select)
* [Render Calendar with specific culture](./globalization)
* [How to change the initial view of the Calendar](./calendar-views)
* [Render Calendar with week numbers](./how-to/render-the-calendar-with-week-numbers)
* [Show other month dates](./how-to/show-dates-of-other-months)
