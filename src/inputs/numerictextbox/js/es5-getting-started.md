---
title: "Getting Started"
component: "NumericTextBox"
description: "Rendering numeric textbox using es5-javascript"
---

# Getting Started

The following section explains the required steps to build the
NumericTextBox component with its basic usage in step by step procedure.

## Dependencies

The following list of dependencies are required to use the NumericTextBox component in your application.

```javascript
|-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-base
```

## Set up your development environment

To get you started with the NumericTextBox component, you can clone the
[Essential JS 2 QuickStart](https://github.com/syncfusion/ej2-quickstart.git) project and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common
settings (`src/styles/styles.css`, `system.config.js` ) to start
with all Essential JS 2 components.

## Add NumericTextBox to the project

Add the HTML input element for the NumericTextBox into your `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 NumericTextBox component</title>
    <!-- Essential JS 2 Input's's dependent material theme -->
  <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
    <link href="//cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>

  <!-- Essential JS 2 all script -->
  <!-- <script src="//cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

  <!-- Essential JS 2 Input's's dependent scripts -->
  <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
  <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
</head>

<body>
    <div>
      <!--element which is going to render the NumericTextBox -->
          <input id="numeric" type="text" />
    </div>

<script>
// initializes NumericTextBox component
var numeric = new ej.inputs.NumericTextBox({
    // sets value to the NumericTextBox
    value: 10
});

// renders initialized NumericTextBox
numeric.appendTo('#numeric');
</script>
</body>

</html>

```

## Run the application

Now use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The below example shows the NumericTextBox.

{% tab template="numeric-textbox/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 NumericTextBox component</title>
    <!-- Essential JS 2 Input's's dependent material theme -->
  <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
    <link href="//cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>

  <!-- Essential JS 2 all script -->
  <!-- <script src="//cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

  <!-- Essential JS 2 Input's's dependent scripts -->
  <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
  <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
</head>

<body>
    <div id='container' style="width: 240px; margin: 0 auto;padding-top:100px;">
            <!--element which is going to render the NumericTextBox -->
          <input id="numeric" type="text" />
    </div>

<script>
// initializes NumericTextBox component
var numeric = new ej.inputs.NumericTextBox({
    // sets value to the NumericTextBox
    value: 10
});

// renders initialized NumericTextBox
numeric.appendTo('#numeric');
</script>
</body>

</html>

```

{% endtab %}

## Range validation

You can set the minimum and maximum range of values in the NumericTextBox using the [`min`](../api/numerictextbox#min) and
[`max`](../api/numerictextbox#max) properties, so the numeric value should be in the min and max range.

The validation behavior depends on the [`strictMode`](../api/numerictextbox#strictmode) property.

The below example demonstrates range validation.

{% tab template="numeric-textbox/es5-getting-started" ,sourceFiles="index.html"%}

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 NumericTextBox component</title>
    <!-- Essential JS 2 Input's's dependent material theme -->
  <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
    <link href="//cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>

  <!-- Essential JS 2 all script -->
  <!-- <script src="//cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

  <!-- Essential JS 2 Input's's dependent scripts -->
  <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
  <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
</head>

<body>
    <div id='container' style="width: 240px; margin: 0 auto;padding-top:100px;">
            <!--element which is going to render the NumericTextBox -->
          <input id="numeric" type="text" />
    </div>

<script>
// initializes NumericTextBox component
var numeric = new ej.inputs.NumericTextBox({
    // sets the minimum range value
    min: 10,
    // sets the maximum range value
    max: 20,
    // sets value to the NumericTextBox
    value: 16,
    // sets the step value to increment or decrement value of the NumericTextBox
    // based on the step value.
    step:2
});

// renders initialized NumericTextBox
numeric.appendTo('#numeric');
</script>
</body>

</html>

```

{% endtab %}

## Formatting the value

User can set the format of the NumericTextBox component using [`format`](../api/numerictextbox#format)
property. The value will be displayed in the specified format, when the component is in focused out state. For more information about
formatting the value, refer to this [link](./formats/).

The below example demonstrates format the value by using currency format value `c2`.

{% tab template="numeric-textbox/es5-getting-started" ,sourceFiles="index.html"%}

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 NumericTextBox component</title>
    <!-- Essential JS 2 Input's's dependent material theme -->
  <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
    <link href="//cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>

  <!-- Essential JS 2 all script -->
  <!-- <script src="//cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

  <!-- Essential JS 2 Input's's dependent scripts -->
  <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
  <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
</head>

<body>
    <div id='container' style="width: 240px; margin: 0 auto;padding-top:100px;">
            <!--element which is going to render the NumericTextBox -->
          <input id="numeric" type="text" />
    </div>

<script>
// initializes NumericTextBox component
var currency = new ej.inputs.NumericTextBox({
    // sets currency with 2 numbers of decimal places format
    format: 'c2',
    // sets value to the NumericTextBox
    value: 10
});

// renders initialized NumericTextBox
currency.appendTo('#numeric');
</script>
</body>

</html>

```

{% endtab %}

## Precision of numbers

You can restrict the number of decimals to be entered in the NumericTextBox by using the [`decimals`](../api/numerictextbox#decimals)
and [`validateDecimalOnType`](../api/numerictextbox#validatedecimalontype) properties.
So, you can't enter the number whose precision is greater than the mentioned decimals.

* If `validateDecimalOnType` is false, number of decimals will not be restricted.
Else, number of decimals will be restricted while typing in the NumericTextBox.

{% tab template="numeric-textbox/es5-getting-started", sourceFiles="index.html"%}

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 NumericTextBox component</title>
    <!-- Essential JS 2 Input's's dependent material theme -->
  <link href="//cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
    <link href="//cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>

  <!-- Essential JS 2 all script -->
  <!-- <script src="//cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script> -->

  <!-- Essential JS 2 Input's's dependent scripts -->
  <script src="//cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
  <script src="//cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
</head>

<body>
    <div id='container'>
        <div style="width: 240px; margin: 0 auto;padding-top:100px;">
          <input id="strict" type="text" />
        </div>
        <div style="width: 240px; margin: 0 auto;padding-top:20px;">
          <input id="allow" type="text" />
        </div>
        </div>
<script>
// initializes NumericTextBox component
var numeric = new ej.inputs.NumericTextBox({
        // restricts number of decimals to be entered in the NumericTextBox
        validateDecimalOnType: true,
        // sets number of decimal places to be allowed by the NumericTextBox
        decimals: 3,
        // sets number with 3 numbers of decimal places format
        format: 'n3',
        value: 10,
        placeholder: 'ValidateDecimalOnType enabled',
        floatLabelType: 'Auto'
});

// renders initialized NumericTextBox
numeric.appendTo('#strict');
var numeric1 = new ej.inputs.NumericTextBox({
        // sets number of decimal places to be allowed by the NumericTextBox
        decimals: 3,
        // sets number with 3 numbers of decimal places format
        format: 'n3',
        value: 10,
        placeholder: 'ValidateDecimalOnType disabled',
        floatLabelType: 'Auto'
});

// renders initialized NumericTextBox
numeric1.appendTo('#allow');
</script>
</body>

</html>

```

{% endtab %}

## See Also

* [How to perform custom validation using FormValidator](./how-to/perform-custom-validation-using-form-validator/)
* [How to customize the UI appearance of the control](./how-to/customize-the-ui-appearance-of-the-control/)
* [How to customize the spin button’s up and down arrow](./how-to/customize-the-spin-buttons-up-and-down-arrow/)
* [How to customize the step value and hide spin buttons](./how-to/customize-the-step-value-and-hide-spin-buttons/)
* [How to prevent nullable input in NumericTextBox](./how-to/prevent-nullable-input-in-numerictextbox/)
* [How to maintain trailing zeros in NumericTextBox](./how-to/maintain-trailing-zeros-in-numerictextbox/)
