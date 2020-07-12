# Populate Data

This section explains how to populate data inputs and provide it to the Maps component.

## Shape Data

The Shape Data collection describing geographical shape information can be obtained from
[GEOJSON format shapes](http://files2.syncfusion.com/dtsupport/uploads/user/uploads/Maps_GeoJSON.zip).

.\ Maps_GeoJSON\All Countries with States

You can assign the complete contents in `“United States of America.json”` file to new JSON object. For better
understanding, a TS file `“usa.ts”` is already created to store JSON data in JSON object “usMap”.

`[usa.ts]`

{% tab compileJsx=true%}

```tsx
export let usMap = //Paste all the content copied from the JSON file//
```

{% endtab %}

## Data Binding

The Maps control supports data binding with the `dataSource` property in the shape layers.

### Properties

The following properties in shape layers is be used for binding data in Maps control,

    * dataSource
    * shapeDataPath
    * shapePropertyPath

## Data Source

The dataSource property is used to represent statistical data in the Maps component, and it accepts a collection of values as input. For example, you can provide a list of objects as input. This data source will be further used to color the map, display data labels, display tooltips, and more.

## Shape Data Path

The `shapeDataPath` property is used to refer the data ID in DataSource. For example, population MapData
contains data ids ‘Name’ and ‘Population’. The `shapeDataPath` and the `shapePropertyPath` properties are
related to each other (refer to `shapePropertyPath` for more details).

## Shape Property Path

The `shapePropertyPath` property is similar to the `shapeDataPath` that refers to the column name in the
`data` property of shape layers to identify the shape. When the values of the `shapeDataPath` property in the
`dataSource` property and the value of `shapePropertyPath` in the data property match, then the associated
object from the `dataSource` is bound to the corresponding shape.

The datasource is populated with JSON data relative to shape data and stored in JSON object. The USA
population as datasource is used for better understanding.

The “populationData.ts” file is used to store JSON data in JSON object “populationData”.

Refer both shape data and datasource as illustrated in the following code example.

`[populationData.ts]`

{% tab compileJsx=true%}

```tsx
export let population_density: object[] = [
       {
                'code': 'AF',
                'value': 53,
                'name': 'Afghanistan',
                'population': 29863010,
                'density': 119
            },
            {
                'code': 'AL',
                'value': 117,
                'name': 'Albania',
                'population': 3195000,
                'density': 111
            },
            {
                'code': 'DZ',
                'value': 15,
                'name': 'Algeria',
                'population': 34895000,
                'density': 15
            },
            {
                'code': 'AO',
                'value': 15,
                'name': 'Angola',
                'population': 18498000,
                'density': 15
            },
            {
                'code': 'AR',
                'value': 15,
                'name': 'Argentina',
                'population': 40091359,
                'density': 14
            },
            {
                'code': 'AM',
                'value': 109,
                'name': 'Armenia',
                'population': 3230100,
                'density': 108
            }
    ];
```

{% endtab %}

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import { population_density } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='name' shapePropertyPath='name' dataSource={population_density}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

<!-- markdownlint-disable MD010 -->

## Binding complex data source

You can bind the data field from data source to the maps in two different ways.

1. Bind the field name directly to the properties as [`shapeDataPath`](../api/maps/layerSettings/#shapedatapath), [`colorValuePath`](../api/maps/markerSettings/#colorvaluepath),
[`valuePath`](../api/maps/tooltipSettings/#valuepath) and [`shapeValuePath`](../api/maps/markerSettings/#shapevaluepath).

2. Bind the field name as `data.field` to the properties as [`shapeDataPath`](../api/maps/layerSettings/#shapedatapath), [`colorValuePath`](../api/maps/markerSettings/#colorvaluepath),
[`valuePath`](../api/maps/tooltipSettings/#valuepath) and [`shapeValuePath`](../api/maps/markerSettings/#shapevaluepath).

The complex data source binding can be done as illustrated in the following code example.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import { complexData } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, MapsTooltip } from '@syncfusion/ej2-react-maps';
import { BubblesDirective, BubbleDirective, Bubble } from '@syncfusion/ej2-react-maps';
import { MarkersDirective, MarkerDirective, Marker } from '@syncfusion/ej2-react-maps';


ReactDOM.render(
            <MapsComponent id="maps">
			<Inject services={[Marker, Bubble, MapsTooltip]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='data.continent' shapePropertyPath='continent' dataSource={complexData}
					shapeSettings={{
					colorValuePath:'data.color'
					}} tooltipSettings={{
						visible: true,
						valuePath: 'data.continent'
					}}>
					<BubblesDirective>
                            <BubbleDirective visible={true} valuePath="data.value"
                            animationDuration={0} opacity={0.8} minRadius={20} maxRadius={90}
							dataSource={[
                                { 'name': 'India', 'value': 18.89685398845257, 'population': 391292635,
                                data: { 'color': 'red', 'population': 391292635,
                                'value': 189685398845257 }
                                }]}
					            tooltipSettings={{
				            		visible: true,
                                    valuePath: 'data.population',
                                    template:"<div>${data.population}</div>"
					            }}/>
                    </BubblesDirective>
					<MarkersDirective>
                        <MarkerDirective visible={true} height={20} animationDuration={0}
                            width={20}  longitudeValuePath= "data.y" latitudeValuePath= "data.x" shapeValuePath= "data.shape" colorValuePath= "data.color"
				            tooltipSettings={{
					            visible: true,
                                valuePath: 'data.name',
                                format: "${data.name}: ${data.x} : ${data.y}"
				            }}
				            offset = {{
				            	y: -10,
                                x: 0
				            }}
                            dataSource={[
                                { latitude: 37.6276571, longitude: -122.4276688,
                                name: 'San Bruno',
                                data: { x: 37.6276571, y: -122.4276688, name: 'San Bruno',
                                shape: 'Pentagon', color: 'red', imageUrl: 'images/ballon.png' }
                                },
                                { latitude: 33.5302186, longitude: -117.7418381, name: 'Laguna Niguel',
                                data: { x: 33.5302186, y: -117.7418381, name: 'Laguna Niguel',
                                color: 'blue', shape: 'Pentagon', imageUrl: 'images/ballon.png' }
                                ]}>
                        </MarkerDirective>
					</MarkersDirective>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}