---
title: "Getting Started"
component: "MaskedTextBox"
description: "Rendering maskedTextBox using typescript"
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
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2 MaskedTextBox" />
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
        <!--input element which needs to be rendered/converted as MaskedTextBox-->
        <input id="mask" type="text" />
    </div>

</body>

</html>

```

Import the MaskedTextBox component into your `app.ts` and append it to the element `#mask` as shown in the following.

`[src/app/app.ts]`

```typescript

import { MaskedTextBox } from '@syncfusion/ej2-inputs';

// initializes the MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox();

mask.appendTo('#mask');

```

## Set the mask

You can set the mask to the MaskedTextBox to validate the user input by using the [`mask`](../api/maskedtextbox#mask) property. To know more about
the usage of mask and configuration, refer to this [link](./mask-configuration/).

The following example demonstrates the usage of mask element `0` that allows any single digit from `0` to `9`.

```typescript

import { MaskedTextBox } from '@syncfusion/ej2-inputs';

// initializes the MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox({
        // sets mask format to the MaskedTextBox
        mask: '000-000-0000'
});

mask.appendTo('#mask');

```

## Run the application

Use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The following example shows the MaskedTextBox with the mask element `0`.

{% tab template="maskedtextbox/getting-started", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", es5Template="mask-default-template" %}

```typescript
import { MaskedTextBox } from '@syncfusion/ej2-inputs';

// initializes the MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox({
        // sets mask format to the MaskedTextBox
        mask: '000-000-0000',
        placeholder: 'MaskedTextBox',
        floatLabelType: 'Always'
});

mask.appendTo('#mask');
```

{% endtab %}

## See Also

* [How to perform custom validation using FormValidator](./how-to/perform-custom-validation-using-form-validator/)
* [How to customize the UI appearance of the control](./how-to/customize-the-ui-appearance-of-the-control/)
* [How to set cursor position while focus on the input textbox](./how-to/set-cursor-position-while-focus-on-the-input-textbox/)
* [How to display numeric keypad when focus on mobile devices](./how-to/display-numeric-keypad-when-focus-on-mobile-devices/)
