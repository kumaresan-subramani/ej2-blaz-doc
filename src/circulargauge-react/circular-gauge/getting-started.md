# Getting Started

This section explains you the steps required to create a simple circular gauge and demonstrate the basic usage of circular gauge control.

## Dependencies

Below is the list of minimum dependencies required to use the circular gauge.

```tsx
|-- @syncfusion/ej2-react-circulargauge
    |-- @syncfusion/ej2-react-base
    |-- @syncfusion/ej2-react-buttons
    |-- @syncfusion/ej2-react-popups
    |-- @syncfusion/ej2-circulargauge
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-popups
```

## Installation and configuration

You can use [`create-react-app`](https://github.com/facebookincubator/create-react-app) to setup the applications.
To install `create-react-app` run the following command.

```sh
npm install -g create-react-app
```

* To setup basic `React` sample use following commands.

<div class='jsx'>

```sh
create-react-app quickstart --scripts-version=react-scripts-ts

cd quickstart

npm install

```

</div>

* Install Syncfusion packages using below command.

```sh
npm install @syncfusion/ej2-react-circulargauge --save
```

* `CircularGauge packages` need to be mapped in `system.config.js` configuration file.

```tsx
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/',
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-circulargauge": "syncfusion:ej2-circulargauge/dist/ej2-circulargauge.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-react-base": "syncfusion:ej2-react-base/dist/ej2-react-base.umd.min.js",
        "@syncfusion/ej2-react-circulargauge": "syncfusion:ej2-react-circulargauge/dist/ej2-react-circulargauge.umd.min.js",
        "@syncfusion/ej2-react-buttons": "syncfusion:ej2-react-buttons/dist/ej2-react-buttons.umd.min.js",
        "@syncfusion/ej2-react-popups": "syncfusion:ej2-react-popups/dist/ej2-react-popups.umd.min.js"
    },
    packages: {
        'app': { main: 'index', defaultExtension: 'tsx' }
    }
});
```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common
settings (`src/styles/styles.css`, `system.config.js` ) to start
with all Essential JS 2 components.

## Run the application

* Now run the application in the browser using the below command.

```cmd
npm start
```

Now, you can start adding CircularGauge component in the application.
For getting started, add the CircularGauge component in `src/App.tsx` file using following code.

```tsx

import * as React from 'react';
import { CircularGaugeComponent } from '@syncfusion/ej2-react-circulargauge';

class App extends React.Component {
render() {
   return (<CircularGaugeComponent></CircularGaugeComponent>);
  }
}
export default App;

```

Now run the `npm start` command in the console, it will run your application and open the browser window.

```sh
npm start
```

the below example shows a basic Circular Gauge.

{% tab template="circulargauge/getting-started", sourceFiles="app/**/*.tsx" ,  isDefaultActive=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(<CircularGaugeComponent id='circulargauge'></CircularGaugeComponent>, document.getElementById('circulargauge'));

```

{% endtab %}

## Set Pointer Value

You can change the pointer value in the above sample using [`value`](../api/circular-gauge/pointer/#value-number) property in [`pointers`](../api/circular-gauge/pointer/).

{% tab template="circulargauge/getting-started", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { CircularGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective } from '@syncfusion/ej2-react-circulargauge';
ReactDOM.render(
  <CircularGaugeComponent id='circulargauge'>
    <AxesDirective>
      <AxisDirective>
        <PointersDirective>
          <PointerDirective value={35}></PointerDirective>
        </PointersDirective>
      </AxisDirective>
    </AxesDirective>
  </CircularGaugeComponent>,document.getElementById('circulargauge'));

```

{% endtab %}