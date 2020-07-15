---
title: "Getting Started"
component: "TimePicker"
description: "This getting started section briefly explains how to create a time picker component in an application."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

Create an app folder `myapp` in local machine to initialize Essential JS 2 JavaScript components.

Using either of the following way to refer the required script and styles.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Step 2:** To render TimePicker component, need to add TimePicker and its dependent packages from below installed location.

#### Dependencies

* ej2-base

* ej2-inputs

* ej2-popups

* ej2-lists

* ej2-calendars

**Syntax:**

> package: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME`

**Example:**

> Package: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-base`
>
> packages: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-inputs`
>
> packages: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-popups`
>
> packages: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-lists`
>
> Package: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-calendars`
>

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title>Essential JS 2 TimePicker Component</title>
    <!-- Essential JS 2 TimePicker's dependent material theme -->
    <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="//cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="//cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css" />

    <!-- Essential JS 2 all script -->
    <!-- <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

    <!-- Essential JS 2 TimePicker's dependent scripts -->
    <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
</head>
<body>
</body>

</html>
```

> If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

**Step 5:** Now, add the `input` element and initiate the `Essential JS 2 TimePicker` component in the `index.html` by using following code

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
    <title>Essential JS 2 TimePicker Component</title>
    <!-- Essential JS 2 TimePicker's dependent material theme -->
    <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="//cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="//cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css" />

    <!-- Essential JS 2 all script -->
    <!-- <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

    <!-- Essential JS 2 TimePicker's dependent scripts -->
    <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
</head>

<body>
    <!-- Add the HTML <input> element  -->
    <input id="element" />
    <script>
        // initialize TimePicker component
        var TimePicker = new ej.calendars.TimePicker();

        // Render initialized TimePicker.
        TimePicker.appendTo('#element')
    </script>
</body>

</html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 TimePicker** component.

### Using CDN link for script and style reference

**Step 1:** The Essential JS 2 components scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Style: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js`](http://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css)
>

**Step 2:** Have to add `CDN` global script and style for calender and its dependent packages in `myapp/index.html` like below.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
    <title>Essential JS 2 Calendar Component</title>
    <!-- Essential JS 2 TimePicker's dependent material theme -->
    <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="//cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="//cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css" />

    <!-- Essential JS 2 all script -->
    <!-- <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

    <!-- Essential JS 2 TimePicker's dependent scripts -->
    <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
    <script src="//cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
</head>

<body>
    <!-- Add the HTML <input> element  -->
    <input id="element" />
    <script>
        // initialize TimePicker component
        var timeObj = new ej.calendars.TimePicker();
        // Render initialized Timepicker.
        timeObj.appendTo('#element')
    </script>
</body>

</html>
```

>When referencing CDN links in application, always ensure the network connection will be in enabled state.

## Setting the time format

Time formats is a way of representing the time value in different string format in textbox and popup
list. By default, the TimePicker's format is based on the culture. You can also customize the format by using the
[`format`](../api/timepicker#format)
property. To know more about the time format standards, refer to the
[Date and Time Format](../../common/internationalization#custom-formats) section.

The following example demonstrates the TimePicker component in 24 hours format with 60 minutes
interval. The time interval is set to
60 minutes by using the [`step`](../api/timepicker#step) property.

{% tab template="timepicker/getting-started", sourceFiles="app.ts,index.html",
es5Template="timepicker-timeformat-template"%}

```typescript
// creates the timepicker component
 var timepicker = new ej.calendars.TimePicker({
        value: new Date(),
        step: 60,
        format: 'HH:mm'
    });
    timepicker.appendTo('#element');
```

{% endtab %}

> Once the time format property is defined, it will be applicable to all the cultures.

## See Also

* [Render TimePicker with min and max time](./time-range)
* [How to achieve validation with TimePicker](./how-to/client-side-validation-using-form-validator)
* [Render TimePicker with specific culture](./globalization)