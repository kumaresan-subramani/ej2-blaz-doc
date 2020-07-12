
# Getting Started

This section explains you the steps required to create a simple circular gauge and demonstrate the basic usage of the circular gauge control.

## Dependencies

Below is the list of minimum dependencies required to use the circular gauge.

```javascript
|-- @syncfusion/ej2-circulargauge
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-popups
```

## Installation and Configuration

* To get you started with circular gauge component, you can clone the
[`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project
and install necessary packages by using the following commands.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

* `CircularGauge packages` need to be mapped in `system.config.js` configuration files.

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
        "@syncfusion/ej2-circulargauge": "syncfusion:ej2-circulargauge/dist/ej2-circulargauge.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});
```

## Add Circular Gauge to the Project

Add the HTML div element for CircularGauge into your `index.html`. `[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>EJ2 Circular Gauge</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Typescript UI Controls" />
    <meta name="author" content="Syncfusion" />
    <link href="index.css" rel="stylesheet" />
    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />
    <!--system js reference and configuration-->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/systemjs/0.19.38/system.js"></script>
    <script src="systemjs.config.js"></script>
</head>

<body>
     <!--container which is going to render the Circular gauge-->
     <div id='container'>
     </div>
</body>

</html>
```

Now import the circular gauge component into your `index.ts` to instantiate a gauge and append the gauge instance to the `#container`

```javascript
import { CircularGauge } from '@syncfusion/ej2-circulargauge';

// initialize CircularGauge component
let gauge: CircularGauge = new CircularGauge();

// render initialized CircularGauge
gauge.appendTo('#container');
```

## Run the application

Now use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The below example shows a basic circular gauge component.

{% tab template= "circular-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5Default" %}

```typescript
import { CircularGauge } from '@syncfusion/ej2-circulargauge';

let gauge: CircularGauge = new CircularGauge();
gauge.appendTo('#element');
```

{% endtab %}

## Set Pointer Value

You can change the pointer value in the above sample using [`value`](../api/circular-gauge/pointer#value-number) property in [`pointers`](../api/circular-gauge/pointer).

{% tab template= "circular-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5PointeValue" %}

```typescript
import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes:[{
        pointers:[{
            value: 35
        }],
    }]
}, '#element');

```

{% endtab %}