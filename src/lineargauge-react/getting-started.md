# Getting Started

<!-- markdownlint-disable MD013 -->

This section explains you the steps required to create a simple linear gauge and demonstrate the basic usage of the linear gauge control.

## Dependencies

Below is the list of minimum dependencies required to use the linear gauge component.

```javascript
+-- @syncfusion/ej2-react-lineargauge
|-- @syncfusion/ej2-lineargauge
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-popups
        |-- @syncfusion/ej2-buttons
|-- @syncfusion/ej2-react-base
```

## Installation and configuration

You can use [`create-react-app`](https://github.com/facebookincubator/create-react-app) to setup the applications.
To install `create-react-app` run the following command.

```sh
npm install -g create-react-app
```

* To setup basic `React` sample use following commands.

<div class='tsx'>

```sh
create-react-app quickstart --scripts-version=react-scripts-ts

cd quickstart

npm install

```

</div>

* Install Syncfusion packages using below command.

```sh
npm install @syncfusion/ej2-react-lineargauge --save
```

## Add Linear Gauge  to the Project

Now, you can start adding LinearGauge component in the application.
For getting started, add the LinearGauge component in `src/index.tsx` file using following code.

{% tab compileJsx=true%}

```tsx

import * as React from 'react';
import { LinearGaugeComponent } from '@syncfusion/ej2-react-lineargauge';

class App extends React.Component {
render() {
   return (<LinearGaugeComponent></LinearGaugeComponent>);
  }
}
export default App;

```

{% endtab %}

## Module Injection

Linear gauge component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature service in the AppModule. In the current application, we are
going to modify the above basic chart to visualize sales data for a particular year.
For this application we are going to use line series, tooltip, data label, category axis and legend
feature of the chart. Please find the relevant feature
service name and description as follows.

* `Annotations` - Inject this module in to `services` to use annotation feature.
* `GaugeTooltip` - Inject this module in to `services` to use tooltip feature.

These modules should be injected to the `services` section as follows,

{% tab compileJsx=true%}

 ```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, Annotations, GaugeTooltip} from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(<LinearGaugeComponent id='gauge'></LinearGaugeComponent>,
 <Inject services={[Annotations, GaugeTooltip]}/>
document.getElementById('gauge'));

```

{% endtab %}

## Add Gauge Title

You can add a title using [`title`](../api/linear-gauge/linearGaugeModel/#title-string) property to the linear gauge to provide quick information to the user.

{% tab template="linear-gauge/getting-started", compileJsx=true, sourceFiles="app/**/*.tsx",  isDefaultActive=true %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge' title='Linear Gauge'>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

## Axis Range

You can set the range to the axis using [`minimum`](../api/linear-gauge/axis/#minimum-number) and [`maximum`](../api/linear-gauge/axis/#maximum-number) properties.

{% tab template="linear-gauge/getting-started", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective minimum={0} maximum={200}>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

To denote the axis values with temperature units, we can add °C as suffix to each label. This can be achieved by setting the {value}°C to the format property of labelStyle in the axis. Here, {value} acts as a placeholder for each axis label.

You can change the pointer value from the default value of the gauge by settings the [`value`](../api/linear-gauge/pointer/#value-number)  property in pointers option in axis.

{% tab template="linear-gauge/getting-started", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective minimum={0} maximum={200} labelStyle={ { format:'{value}°C' } }>
                <PointersDirective>
                    <PointerDirective value={140}>
                    </PointerDirective>
                </PointersDirective>
                <RangesDirective>
                    <RangeDirective start={0} end={80} startWidth={15} endWidth={15}>
                    </RangeDirective>
                    <RangeDirective start={80} end={120} startWidth={15} endWidth={15}>
                    </RangeDirective>
                    <RangeDirective start={120} end={140} startWidth={15} endWidth={15}>
                    </RangeDirective>
                    <RangeDirective start={140} end={200} startWidth={15} endWidth={15}>
                    </RangeDirective>
                </RangesDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}

## Set Pointer Value

You can change the pointer value in the below sample using [`value`](../api/linear-gauge/pointer/#value-number) property in [`pointers`](../api/linear-gauge/pointer/).

{% tab template="linear-gauge/getting-started", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { LinearGaugeComponent, AxesDirective, AxisDirective, PointersDirective, PointerDirective } from '@syncfusion/ej2-react-lineargauge';

ReactDOM.render(
    <LinearGaugeComponent id='gauge'>
        <AxesDirective>
            <AxisDirective minimum={0} maximum={200}>
                <PointersDirective>
                    <PointerDirective value={140} color='green'>
                    </PointerDirective>
                </PointersDirective>
            </AxisDirective>
        </AxesDirective>
    </LinearGaugeComponent>,document.getElementById('gauge'));

```

{% endtab %}