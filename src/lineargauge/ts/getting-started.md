# Getting Started

This section explains you the steps required to create a simple linear gauge and demonstrate the basic usage of the linear gauge control.

## Dependencies

Below is the list of minimum dependencies required to use the linear gauge.

```javascript
|-- @syncfusion/ej2-lineargauge
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-popups
```

## Installation and Configuration

* To get the started with LinearGauge component, you can clone the
[`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project
and install necessary packages by using the following commands.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

* LinearGauge packages need to be mapped in `system.config.js` configuration file.

```javascript
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/',
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-lineargauge": "syncfusion:ej2-charts/dist/ej2-lineargauge.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});
```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common
settings (`system.config.js` ) to start
with all Essential JS 2 components.

## Add Linear Gauge to the Project

Add the HTML div element for linear gauge into your `index.html`. `[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>EJ2 Linear gauge</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Typescript UI Controls" />
    <meta name="author" content="Syncfusion" />
    <link href="index.css" rel="stylesheet" />
    <!--system js reference and configuration-->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/systemjs/0.19.38/system.js"></script>
    <script src="systemjs.config.js"></script>
</head>

<body>
     <!-- container which is going to render the linear gauge -->
     <div id='container'>
     </div>
</body>

</html>
```

Now import the LinearGauge component into your `index.ts` to initialize a linear gauge and append the linear gauge instance to the `#container`.

```javascript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';

// initialize linear gauge component
let gauge: LinearGauge = new LinearGauge();

// render initialized linear gauge
gauge.appendTo('#container');
```

Now use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The below example shows a basic linear gauge component.

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5Default" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';

let gauge: LinearGauge = new LinearGauge();
gauge.appendTo('#element');

```

{% endtab %}

## Module Injection

LinearGauge component is segregated into individual feature-wise modules. In order to use a particular feature, you need to inject its feature module using `LinearGauge.Inject()` method. For this application,  we are going to use tooltip and annotation feature of the linear gauge. Please find relevant feature module name and description as follows.

* Annotation -  Inject this module to use the annotation features.
* GaugeTooltip - Inject this module to use the tooltip features.

Now import the above mentioned modules from linear gauge package and inject it into the LinearGauge component using `LinearGauge.Inject` method.

```typescript
import { GaugeTooltip, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations, GaugeTooltip);

```

## Add Gauge Title

You can add a title using [`title`](../api/linear-gauge/linearGaugeModel#title-string) property to the linear gauge to provide quick information to the user.

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5GaugeTitle" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    // Title for linear gauge
    title: 'linear gauge'
}, '#element');

```

{% endtab %}

## Axis Range

You can set the range to the axis using [`minimum`](../api/linear-gauge/axis#minimum-number) and [`maximum`](../api/linear-gauge/axis#maximum-number) properties.

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5AxisRange" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes: [{
        minimum: 0,
        maximum: 200
    }]
}, '#element');

```

{% endtab %}

To denote the axis values with temperature units, we can add °C as suffix to each label. This can be achieved by setting the {value}°C to the format property of labelStyle in the axis. Here, {value} acts as a placeholder for each axis label.

You can change the pointer value from the default value of the gauge by settings the [`value`](../api/linear-gauge/pointer/#value-number)  property in pointers option in axis.

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html",es5Template="es5AxisCustomization" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes: [{
        minimum: 0,
        maximum: 200,
        pointers: [{
            value: 140
        }],
        labelStyle: {
            format: '{value}°C'
        },
        ranges: [{
            start: 0,
            end: 80,
            startWidth:15,
            endWidth:15
        }, {
            start: 80,
            end: 120,
            startWidth:15,
            endWidth:15
        }, {
            start: 120,
            end: 140,
            startWidth:15,
            endWidth:15
        }, {
            start: 140,
            end: 200,
            startWidth:15,
            endWidth:15
        }]
    }]
}, '#element');

```

{% endtab %}

## Set Pointer Value

You can change the pointer value in the below sample using [`value`](../api/linear-gauge/pointer/#value-number) property in [`pointers`](../api/linear-gauge/pointer).

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5SetPointer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes:[{
        pointers:[{
            value: 40,
            color: 'green'
        }]
    }]
}, '#element');

```

{% endtab %}