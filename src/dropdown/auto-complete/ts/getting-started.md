---
title: "Autocomplete Getting started"
component: "AutoComplete"
description: "This section explains how to create a simple Syncfusion JavaScript autocomplete control and configure it's functionalities in TypeScript."
---

# Getting started

This section explains how to create a simple **AutoComplete** component and configure its
available functionalities in TypeScript, using Essential JS 2
[quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.

## Dependencies

The following list of dependencies are required to use the AutoComplete component in your application.

```javascript
|-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-buttons
```

## Set up of the development environment

To get started with the AutoComplete component, you have to clone the Essential JS 2
[`quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and install the npm packages by using the following commands.

```shell

git clone https://github.com/syncfusion/ej2-quickstart.git quickstart

cd quickstart

npm install

```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common settings
(`src/styles/styles.css`, `system.config.js`) to start all the Essential JS 2 components.

## Initialize the AutoComplete

The AutoComplete can be initialized through input tags.

Add the HTML input element which needs to be initialized as AutoComplete in `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 AutoComplete component</title>
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
        <!--element which is going to render the AutoComplete-->
        <input type="text" tabindex="1" id='atcelement' />
    </div>

</body>

</html>
```

Now import the AutoComplete component to your `app.ts` and initialize it to the element `#atcelement` as
shown below.

`[src/app/app.ts]`

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

// initialize AutoComplete component
let atcObject: AutoComplete = new AutoComplete();

// render initialized AutoComplete
atcObject.appendTo('#atcelement');

```

## Binding data source

After initialization, populate the AutoComplete with data using the
[`dataSource`](/auto-complete/api-autoComplete.html#datasource) property.
Here, an array of string values is passed to the AutoComplete component.

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

// define the array of data
let sportsData: string[] = ['Badminton', 'Basketball', 'Cricket', 'Football', 'Golf', 'Gymnastics', 'Hockey', 'Rugby', 'Snooker', 'Tennis'];

// initialize AutoComplete component
let atcObject: AutoComplete = new AutoComplete({
    //set the data to dataSource property
    dataSource: sportsData
});

// render initialized AutoComplete
atcObject.appendTo('#atcelement');

```

## Run the application

After completing the configuration required to render a basic AutoComplete, run the following command to display the output in your default browser.

```cmd

 npm run start

```

The following example illustrates the output in your browser.

{% tab template="autocomplete/getting-started", isDefaultActive = "true", es5Template="basic",sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: string[] = ['Badminton', 'Basketball', 'Cricket', 'Football', 'Golf', 'Gymnastics', 'Hockey', 'Tennis'];

// initialize AutoComplete component
let atcObject: AutoComplete = new AutoComplete({
    //set the data to dataSource property
    dataSource: sportsData,
    // set placeholder to AutoComplete input element
    placeholder: "Find a game"
});

// render initialized AutoComplete
atcObject.appendTo('#atcelement');
```

{% endtab %}

## Custom values

The AutoComplete allows the user to give input as custom value which is not required to present in
predefined set of values. By default, this support is enabled by
[`allowCustom`](/auto-complete/api-autoComplete.html#allowcustom) property.
The custom value will be sent to post back handler when a form
is about to be submitted.

{% tab template="autocomplete/getting-started", es5Template="basic-customvalue", sourceFiles="app.ts,index.html" %}

```typescript
import { AutoComplete } from '@syncfusion/ej2-dropdowns';

// defined the array of data
let sportsData: { [key: string]: Object }[] = [
    { Id: 'Game1', Game: 'Badminton' },
    { Id: 'Game2', Game: 'Basketball' },
    { Id: 'Game3', Game: 'Cricket' },
    { Id: 'Game4', Game: 'Football' },
    { Id: 'Game5', Game: 'Golf' },
    { Id: 'Game6', Game: 'Hockey' },
    { Id: 'Game7', Game: 'Rugby' },
    { Id: 'Game8', Game: 'Snooker' }
];

// initialize AutoComplete component
let atcObject: AutoComplete = new AutoComplete({
    //set the data to dataSource property
    dataSource: sportsData,
    // By default, its enabled. For your better understanding, showcase this property.
    allowCustom: true,
    // maps the appropriate column to fields property
    fields: { value: 'Game' },
    // set placeholder to AutoComplete input element
    placeholder: "Find a game"
});

// render initialized AutoComplete
atcObject.appendTo('#atcelement');
```

{% endtab %}

## Configure the suggestion list

By default, suggestion list width automatically adjusts according to the AutoComplete input element's width, and the height of the suggestion list has '300px'.

The height and width of the popup list can also be customized using the
[`popupHeight`](/auto-complete/api-autoComplete.html#popupheight) and
[`popupWidth`](/auto-complete/api-autoComplete.html#popupwidth) property respectively.

In the following sample, suggestion list's width and height are configured.

{% tab template="autocomplete/getting-started", es5Template="basic-suggestion", sourceFiles="app.ts,index.html" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';

// define the array of data
let sportsData: string[] = ['Badminton', 'Basketball', 'Cricket', 'Football', 'Golf', 'Gymnastics', 'Hockey', 'Rugby', 'Snooker', 'Tennis'];

// initialize AutoComplete component
let atcObject: AutoComplete = new AutoComplete({
    //set the data to dataSource property
    dataSource: sportsData
    //set width to suggestion list
    popupWidth: '250px',
    // set placeholder to AutoComplete input element
    placeholder: "Find a game",
    // set the popup list height
    popupHeight: "250px"
});

// render initialized AutoComplete
atcObject.appendTo('#atcelement');
```

{% endtab %}

## See Also

* [How to bind the data](./data-binding)