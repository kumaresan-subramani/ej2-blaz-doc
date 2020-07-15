---
title: "Combo box Getting started"
component: "ComboBox"
description: "This section explains how to create a simple Syncfusion JavaScript combo box control and configure its functionalities in TypeScript."
---

# Getting Started

This section explains how to create a simple **ComboBox** component and configure its available functionalities in TypeScript, using Essential JS 2 [quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.

## Dependencies

The following list of dependencies are required to use the `ComboBox` component in your application.

```javascript
|-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-buttons
```

## Set up of the development environment

To get you started with ComboBox component, you need to clone the
[`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and
install the packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common
settings (`src/styles/styles.css`, `system.config.js` ) to start
with all Essential JS 2 components.

## Initialize the ComboBox

The ComboBox can be initialized through three different tags which described in [Initialize Tags](../tags.html).

Add the HTML input element that needs to be initialized as ComboBox in `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 ComboBox component</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <div id='container' style="margin:0 auto; width:300px;">
        <!--element which is going to render the ComboBox-->
        <input type="text" tabindex="1" id='comboelement' />
    </div>

</body>

</html>
```

Now, import the  ComboBox component to your `app.ts` and initialize it to the element `#comboelement` as shown below.

`[src/app/app.ts]`

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox();

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');

```

## Binding data source

After initializing, populate the ComboBox with data using the [dataSource](/combo-box/api-comboBox.html#datasource) property.
Here, an array of string values is passed to the ComboBox component.

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

// define the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox({
    //set the data to dataSource property
    dataSource: sportsData
});

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');
```

## Run the application

After completing the configuration required to render a basic ComboBox, run the following command to
display the output in your default browser.

```cmd
npm run start
```

The following example illustrates the output in your browser.

{% tab template="combobox/getting-started", isDefaultActive = "true", es5Template="basic", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to ComboBox input element
    placeholder: "Select a game"
});

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');
```

{% endtab %}

## Custom values

The ComboBox allows the user to give input as custom value which is not required to present in predefined
set of values. By default, this support is enabled by [allowCustom](/combo-box/api-comboBox.html#allowcustom)
 property. In this case, both text field and value field considered as same.
The custom value will be sent to post back handler when a form is about to be submitted.

{% tab template="combobox/getting-started", es5Template="basic-customvalue", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: { [key: string]: Object }[] = [
    { Id: 'game1', Game: 'Badminton' },
    { Id: 'game2', Game: 'Football' },
    { Id: 'game3', Game: 'Tennis' }
];

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox({
    //set the data to dataSource property
    dataSource: sportsData,
    // By default, its enabled. For your better understanding, showcase this property here.
    allowCustom: true,
    // maps the appropriate column to fields property
    fields: { text: 'Game', value: 'Id' },
    // set placeholder to ComboBox input element
    placeholder: "Select a game"
});

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');
```

{% endtab %}

## Configure the popup list

By default, the width of the popup list automatically adjusts according to the ComboBox input element's width, and the height of the popup list has '300px'.

The height and width of the popup list can also be customized using the
[popupHeight](/combo-box/api-comboBox.html#popupheight)
&nbsp;and [popupWidth](/combo-box/api-comboBox.html#popupwidth) properties
respectively.

In the following sample, popup list's width and height are configured.

{% tab template="combobox/getting-started", es5Template="basic-suggestion", sourceFiles="app.ts,index.html" %}

```typescript
import { ComboBox } from '@syncfusion/ej2-dropdowns';

// define the array of data
let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];

// initialize ComboBox component
let comboBoxObject: ComboBox = new ComboBox({
    //set the data to dataSource property
    dataSource: sportsData,
    //set height to popup list
    popupHeight: '200px',
    //set width to popup list
    popupWidth: '250px',
    // set placeholder to ComboBox input element
    placeholder: "Select a game"
});

// render initialized ComboBox
comboBoxObject.appendTo('#comboelement');
```

{% endtab %}

## See Also

* [How to bind the data](./data-binding)
* [How to initialize the control using different tags](./tags)