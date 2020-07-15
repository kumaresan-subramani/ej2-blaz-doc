---
title: "Getting Started"
component: "Textbox"
description: "Helps to get started with text box component along with its key features such as a floating label, adding icons (input group), and ripple effect."
---

# Getting Started

This section briefly explains about how to create a simple TextBox through CSS classes using Essential JS 2 quickstart seed repository.

## Dependencies

The following list of dependencies are required to use the TextBox component in your application.

```js
|-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-base

```

## Installation and configuration

* Clone the Essential JS 2 quickstart application project from
[GitHub](https://github.com/syncfusion/ej2-quickstart.git) and
install necessary npm packages using the following command.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> By default, the project is configured with all the Essential JS 2 dependencies. For better understanding, remove all the dependencies from
`src/system.config.js` to get started with the TextBox component.

* Refer to the [TextBox component dependencies](#dependencies) in `system.config.js` configuration file.

`[src/system.config.js]`

```js
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/',
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});

System.import('app');
```

* The TextBox CSS files are available in the `ej2-inputs` package folder.
This can be referenced in your application using the following code.

`[src/styles/styles.css]`

```css
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
```

> The [Custom Resource Generator (CRG)](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific components.
> This web tool is useful to combine the required component scripts and styles in a single file.

## Adding TextBox to the application

Add the HTML Input element with `e-input` class into your `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 TextBox </title>
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
      <!--element which is going to render the TextBox-->
      <input class="e-input" type="text" placeholder="Enter Date" />
    </div>
</body>

</html>

```

## Adding icons to the TextBox

You can create a TextBox with icon as a group by creating the parent div element with the class `e-input-group` and add the icon element as span with the class `e-input-group-icon`. For detailed information, refer to the [Groups](./groups/) section.

```html
      <!--element which is going to render the TextBox with date icon-->
      <div class="e-input-group">
            <input class="e-input" name='input' type="text" placeholder="Enter Date"/>
            <span class="e-input-group-icon e-input-popup-date"></span>
      </div>
```

* Now, run the application in the browser using the following command.

```shell
npm start
```

Output will be as follows:

{% tab template= "textbox/icon-samples", sourceFiles="index.html,index.ts,index.css", isDefaultActive=true, es5Template="icon-template" %}

```html
        <input class="e-input" type="text" placeholder="Enter Date" />
        <div class="e-input-group">
            <input class="e-input" name='input' type="text" placeholder="Enter Date"/>
            <span class="e-input-group-icon e-input-popup-date"></span>
        </div>

```

{% endtab %}

## Floating label

The floating label TextBox floats the label above the TextBox after focusing, or filled with value in the TextBox.

You can create the floating label TextBox by using the [floatLabelType](../api/textbox/#floatLabelType) API.

{% tab template= "textbox/textbox-component", sourceFiles="index.html,index.ts,index.css", es5Template="clear-icon-template" %}

{% endtab %}

## See Also

* [How to render TextBox programmatically](./how-to/add-textbox-programmatically)
* [How to add floating label to TextBox programmatically](./how-to/add-floating-label-to-textbox-programmatically)
