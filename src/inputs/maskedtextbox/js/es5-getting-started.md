---
title: "Getting Started"
component: "MaskedTextBox"
description: "Rendering masked textBox using es5-javascript"
---

# Getting Started

The following section explains the required steps to build the
MaskedTextBox component with its basic usage in step-by-step procedure.

## Dependencies

The following list of dependencies are required to use the MaskedTextBox component in your application.

```javascript
|-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-base
```

## Set up your development environment

To get started with MaskedTextBox component, you can clone the
[Essential JS 2 QuickStart](https://github.com/syncfusion/ej2-quickstart.git) project, and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with the common
settings (`src/styles/styles.css`, `system.config.js` ) to start
with all the Essential JS 2 components.

## Add MaskedTextBox to the project

Add the HTML input element that needs to be rendered as MaskedTextBox in the `index.html` file.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 MaskedTextBox</title>
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
    <div style="margin: 50px;">
        <!--input element which needs to be rendered/converted as MaskedTextBox-->
        <input id="mask" type="text" />
    </div>

<script>
// initializes the MaskedTextBox component
var mask = new ej.inputs.MaskedTextBox();

mask.appendTo('#mask');
</script>
</body>

</html>

```

## Set the mask

You can set the mask to the MaskedTextBox to validate the user input by using the [`mask`](../api/maskedtextbox#mask) property. To know more about
the usage of mask and configuration, refer to this [link](./mask-configuration/).

The following example demonstrates the usage of mask element `0` that allows any single digit from `0` to `9`.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 MaskedTextBox</title>
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
    <div style="margin: 50px;">
        <!--input element which needs to be rendered/converted as MaskedTextBox-->
        <input id="mask" type="text" />
    </div>

<script>
// initializes the MaskedTextBox component and sets mask format
var mask = new ej.inputs.MaskedTextBox({mask: '000-000-0000'});

mask.appendTo('#mask');
</script>
</body>

</html>

```

## Run the application

Use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The following example shows the MaskedTextBox with the mask element `0`.

{% tab template="maskedtextbox/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html"%}

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 MaskedTextBox</title>
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
    <div id='container' style="width: 240px; margin: 0 auto;">
            <input id="mask" type="text" />
        </div>

<script>
// initializes the MaskedTextBox component and sets mask format
var mask = new ej.inputs.MaskedTextBox({mask: '000-000-0000', placeholder: 'MaskedTextBox', floatLabelType: 'Always'});

mask.appendTo('#mask');
</script>
</body>

</html>

```

{% endtab %}

## See Also

* [How to perform custom validation using FormValidator](./how-to/perform-custom-validation-using-form-validator/)
* [How to customize the UI appearance of the control](./how-to/customize-the-ui-appearance-of-the-control/)
* [How to set cursor position while focus on the input textbox](./how-to/set-cursor-position-while-focus-on-the-input-textbox/)
* [How to display numeric keypad when focus on mobile devices](./how-to/display-numeric-keypad-when-focus-on-mobile-devices/)
