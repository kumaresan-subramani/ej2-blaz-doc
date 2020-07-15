---
title: "Drop-down tree Getting started"
component: "Dropdown Tree"
description: "This section explains how to create a simple Syncfusion JavaScript drop-down tree control and configure it's functionalities in TypeScript."
---

# Getting Started

This section explains you about how to create a simple **Dropdown Tree** control and configure its available
functionalities in TypeScript using the Essential JS 2 [quickstart](https://github.com/syncfusion/ej2-quickstart.git).

## Dependencies

The following list of dependencies are required to use the Dropdown Tree control in your application.

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

To get started with the Dropdown Tree control, you have to clone the Essential JS 2 [`quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and install the npm packages by using the following commands.

```shell
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is pre-configured with the common
settings (`src/styles/styles.css`, `system.config.js` ) to start
all the Essential JS 2 controls.

## Initialize the Dropdown Tree

Add the HTML input element that needs to be initialized as a Dropdown Tree in `index.html`.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 Dropdown Tree control</title>
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
        <!--element which is going to render the Dropdown Tree-->
        <input type="text" tabindex="1" id='ddltreeelement' />
    </div>

</body>

</html>
```

Now, import the  Dropdown Tree control to your `app.ts` and initialize it to the element `#ddltreeelement` as shown below.

`[src/app/app.ts]`

```typescript

import { DropDownTree } from '@syncfusion/ej2-dropdowns';

// initialize Dropdown Tree control
let DropDownTreeObject: DropDownTree = new DropDownTree();

// render initialized Dropdown Tree
DropDownTreeObject.appendTo('#ddltreeelement');

```

## Binding data source

The Dropdown Tree control can load the data either from local data sources or remote data services. This can be done using the `dataSource` property that is a member of the `fields` property. The dataSource property supports array of JavaScript objects and DataManager. Here, an array of JSON values is passed to the Dropdown Tree control.

```typescript
import { DropDownTree } from '@syncfusion/ej2-dropdowns';

//define the array of JSON
let data: { [key: string]: Object }[] = [
    {
        nodeId: '01', nodeText: 'Music',
        nodeChild: [
            { nodeId: '01-01', nodeText: 'Gouttes.mp3' }
        ]
    },
    {
        nodeId: '02', nodeText: 'Videos', expanded: true,
        nodeChild: [
            { nodeId: '02-01', nodeText: 'Naturals.mp4' },
            { nodeId: '02-02', nodeText: 'Wild.mpeg' },
        ]
    },
    {
        nodeId: '03', nodeText: 'Documents',
        nodeChild: [
            { nodeId: '03-01', nodeText: 'Environment Pollution.docx' },
            { nodeId: '03-02', nodeText: 'Global Water, Sanitation, & Hygiene.docx' },
            { nodeId: '03-03', nodeText: 'Global Warming.ppt' },
            { nodeId: '03-04', nodeText: 'Social Network.pdf' },
            { nodeId: '03-05', nodeText: 'Youth Empowerment.pdf' },
        ]
    },
];

// initialize Dropdown Tree control
let DropDownTreeObject: DropDownTree = new DropDownTree({
    //binding data source through fields property
    fields: { dataSource: data, value: 'nodeId', text: 'nodeText', child: 'nodeChild' }
});

// render initialized Dropdown Tree
DropDownTreeObject.appendTo('#ddltreeelement');
```

## Run the application

After completing the configuration required to render a basic Dropdown Tree, run the following command to
display the output in your default browser.

```cmd
npm run start
```

The following example explains the output in your browser.

{% tab template="dropdowntree/getting-started", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html" %}

```typescript
import { DropDownTree } from '@syncfusion/ej2-dropdowns';

//define the array of JSON
let data: { [key: string]: Object }[] = [
    {
        nodeId: '01', nodeText: 'Music',
        nodeChild: [
            { nodeId: '01-01', nodeText: 'Gouttes.mp3' }
        ]
    },
    {
        nodeId: '02', nodeText: 'Videos', expanded: true,
        nodeChild: [
            { nodeId: '02-01', nodeText: 'Naturals.mp4' },
            { nodeId: '02-02', nodeText: 'Wild.mpeg' },
        ]
    },
    {
        nodeId: '03', nodeText: 'Documents',
        nodeChild: [
            { nodeId: '03-01', nodeText: 'Environment Pollution.docx' },
            { nodeId: '03-02', nodeText: 'Global Water, Sanitation, & Hygiene.docx' },
            { nodeId: '03-03', nodeText: 'Global Warming.ppt' },
            { nodeId: '03-04', nodeText: 'Social Network.pdf' },
            { nodeId: '03-05', nodeText: 'Youth Empowerment.pdf' },
        ]
    },
];

// initialize Dropdown Tree control
let DropDownTreeObject: DropDownTree = new DropDownTree({
    //binding data source through fields property
    fields: { dataSource: data, value: 'nodeId', text: 'nodeText', child: 'nodeChild' }
    // set placeholder to Dropdown Tree input element
    placeholder: "Select a Item"
});

// render initialized Dropdown Tree
DropDownTreeObject.appendTo('#ddltreeelement');
```

{% endtab %}