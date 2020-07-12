# Getting Started

This section explains you the steps required to create a map and demonstrate the basic usage of the maps control.

You can explore some useful features in the Maps component using the following video.

`youtube:kwE6ikF7QYQ`

## Dependencies

Below is the list of minimum dependencies required to use the Maps.

```javascript
|-- @syncfusion/ej2-react-maps
    |-- @syncfusion/ej2-maps
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-react-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-react-buttons
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-react-popups
```

## Installation and Configuration

* You can use [`create-react-app`](https://github.com/facebook/create-react-app) to setup the applications.
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
npm install @syncfusion/ej2-react-maps --save
```

## Add Map to the Project

Now import the Maps component into your `src/App.tsx` to instantiate a map.

{% tab compileJsx=true%}

```tsx
import * as React from 'react';
import { MapsComponent } from '@syncfusion/ej2-react-maps';

class App extends React.Component {
render() {
   return (<MapsComponent id="container" />);
  }
}
export default App;
```

{% endtab %}

Now use the `npm start` command to run the application in the browser.

```cmd
npm start
```

The below example shows this.

{% tab compileJsx=true%}

```tsx
import * as React from 'react';
import { MapsComponent } from '@syncfusion/ej2-react-maps';

class App extends React.Component {
render() {
   return (<MapsComponent id="container" />);
  }
}
export default App;
```

{% endtab %}

As we didn't specify shapeData to the maps, no shape will be rendered and only an empty SVG element is appended to the maps container.

## Module Injection

Maps component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature services using `Inject` tag.  Find the modules available in maps and its description as follows.

* Annotations - Inject this provider to use annotations feature.
* Bubble - Inject this provider to use bubble feature.
* DataLabel - Inject this provider to use data label feature.
* Highlight - Inject this provider to use highlight feature.
* Legend - Inject this provider to use legend feature.
* Marker - Inject this provider to use marker feature.
* MapsTooltip - Inject this provider to use tooltip series.
* NavigationLine - Inject this provider to use navigation lines feature.
* Selection - Inject this provider to use selection feature.
* Zoom - Inject this provider to use zooming and panning feature.

For this application we are going to use tooltip, data label and legend features of the maps.
Now import the MapsTooltip, DataLabel and Legend modules from maps package and inject it into the
Maps component using `Inject` tag with required services.

{% tab compileJsx=true%}

```tsx

import { Maps, Legend, DataLabel, MapsTooltip } from '@syncfusion/ej2-maps';
import * as React from 'react';
import { MapsComponent } from '@syncfusion/ej2-react-maps';

class App extends React.Component {
render() {
   return (
    <MapsComponent id="element">
        <Inject services={[DataLabel, Legend, MapsTooltip]} />
    </MapsComponent>);
  }
}
export default App;

```

{% endtab %}

## Render shapes from GeoJSON data

This section explains how to bind GeoJSON data to the map.

{% tab compileJsx=true%}

```tsx

let usMap: Object =
{
    "type": "FeatureCollection",
    "crs": { "type": "name", "properties": { "name": "urn:ogc:def:crs:OGC:1.3:CRS84" } },
    "features": [
        { "type": "Feature", "properties": { "iso_3166_2": "MA", "name": "Massachusetts", "admin": "United States of America" }, "geometry": { "type": "MultiPolygon", "coordinates": [ [ [ [ -70.801756294617277, 41.248076234530558 ]] ] ] }
        }
    ]
    //..
};

```

{% endtab %}

Elements in the maps will get rendered in the layers. So add a layer collection to the maps by using [`layers`]property.
Now bind the GeoJSON data to the [`shapeData`] property.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Bind data source to map

The following properties in layers are used for binding data source to map.

* [`dataSource`]
* [`shapeDataPath`]
* [`shapePropertyPath`]

The [`dataSource`] property takes collection value as input. For example, the list of objects can be provided as input.
This data is further used in tooltip, data label, bubble, legend and in color mapping.

The [`shapeDataPath`] property used to refer the data ID in dataSource. Where as, the [`shapePropertyPath`] property is used to refer
the column name in shapeData to identify the shape. Both the properties are related to each other. When the values of the
shapeDataPath property in the dataSource property and the value of shapePropertyPath in the shapeData property match, then the
associated object from the dataSource is bound to the corresponding shape.

The JSON object "electionData" is used as data source below.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import { uncountries } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='Country' shapePropertyPath='name' dataSource={uncountries}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Apply Color Mapping

The Color Mapping feature supports customization of shape colors based on the underlying value of shape received from bounded data.
Specify the field name from which the values have to be compared for the shapes in [`colorValuePath`] property in [`shapeSettings`].

Specify color and value in [`colorMapping`] property. Here '#D84444' is specified for 'Trump' and '#316DB5' is specified for 'Clinton'.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { uncountries } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='Country' shapePropertyPath='name' dataSource={uncountries}
                        shapeSettings={ {
                            colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Add Title for Maps

You can add a title using [`titleSettings`] property to the map to provide quick
information to the user about the shapes rendered in the map.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { uncountries } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps"  titleSettings={ { text: 'World map with membership' } }>
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='Country' shapePropertyPath='name' dataSource={uncountries}
                        shapeSettings={ {
                            colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Enable Legend

You can show legend for the maps by setting true to the [`visible`]
property in [`legendSettings`] object and by injecting the `Legend`
service using `Inject` tag.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { uncountries } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" legendSettings={ { visible: true } } >
            <Inject services={[Legend]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='Country' shapePropertyPath='name' dataSource={uncountries}
                        shapeSettings={ {
                            colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Add Data Label

You can add data labels to show additional information of the shapes in map. This can be achieved by
setting [`visible`] property to true in the [`dataLabelSettings`] object and by injecting `DataLabel` service using `Inject` tag.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, DataLabel } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[DataLabel]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                     dataLabelSettings={ {
                            visible: true,
                            labelPath: 'name',
                            smartLabelMode: 'Trim'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Enable Tooltip

The tooltip is useful when you cannot display information by using the data labels due to space constraints.
You can enable tooltip by setting the [`visible`] property as true in [`tooltipSettings`] object and by
injecting `MapsTooltip` service using `Inject` tag.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, MapsTooltip } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[MapsTooltip]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                     tooltipSettings={ {
                            visible: true,
                            valuePath: 'name'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}