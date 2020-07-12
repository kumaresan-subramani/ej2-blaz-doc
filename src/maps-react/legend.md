# Legend

A legend is a key used on a map that contains swatches of symbols with descriptions. It provides valuable
information for interpreting what the map is displaying and can be represented in various colors, shapes or
other identifiers based on the data. It gives a breakdown of what each symbol represents throughout the map.

## Visibility

The Legends can be made visible by setting the visible property of legendSettings to true.

## Positioning the Legend

The legend can be positioned in two ways.

* Absolute Position.

* Dock Position.

### Absolute Position

Based on the margin values of X and Y-axes, the Map legends can be positioned with the support of `location.x`
and `location.y` properties available in legendSettings. For positioning the legend based on margins
corresponding to a map, position value is set as ‘Float’.

### Dock Position

The map legends can be positioned in following locations within the container.
You can set this option by using `position` property in legendSettings.

    1 Top

    2 Left

    3 Bottom

    4 Right

above four positions can be aligned combination of 'Near', 'Center' and 'Far' using `alignment` in
`legendSettings`. So legend can be aligned 12 positions.

## Legend Mode

Legend had two type of mode. `Default` mode and `Interactive` mode.

### Default Mode

Default mode legends having symbols with legend labels, used to identify the shape or bubble or marker color.

### Interactive Mode

The legends can be made interactive with an arrow mark indicating the exact range color in the legend when the
mouse hovers over the corresponding shapes. You can enable this option by setting `mode` property in
legendSettings value as “Interactive” and default value of `mode` property is “Default” to enable the normal legend.

## Legend Size

The map legend size can be modified by using the `height` and `width` properties in `legendSettings`.

## Legend for Shapes

The Layer shape type legends can be generated for each color mappings in shape settings.
**Note:** Below code snippet demonstrate the equal colormapping legends for the shapes.

Create the electiondata.ts file with following data for layer `dataSource`.

{% tab compileJsx=true%}

```tsx
export var UNcountries: Object[] =
[
    {  "Country": "China", "Membership": "Permanent"},
            {"Country": "France","Membership": "Permanent" },
            { "Country": "Russia","Membership": "Permanent"},
            {"Country": "Kazakhstan","Membership": "Non-Permanent"},
            { "Country": "Poland","Membership": "Non-Permanent"},
            {"Country": "Sweden","Membership": "Non-Permanent"}
    ];
```

{% endtab %}

Import the 'electionData' and assign for the layer `dataSource`. Provide the `shapePropertyPath` value as 'name
and `shapeDataPath` value as 'State'.

To enable the equal colormapping refer the `shapeSettings.colorMapping` code snippet.

Finally set `legendSettings.visible` as true and Inject the Legend Module into Maps using
`<Inject services={[Legend]}/>` tag.

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

## Legend Shape

To get the legend shape value for `legendSettings` by using `shape` property. You can customize the shape by
using the `shapeWidth` and `shapeHeight` property.

## Legend for items excluded from color mapping

Based on the ranges in data source, get the excluded ranges from color mapping, and then show the legend with excluded range values are bound to the specific legend.

The following code example shows legends for the items excluded from color mapping.

Finally set `legendSettings.visible` as true and Inject the Legend Module into Maps using
`<Inject services={[Legend]}/>` tag.

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
                            from: 0, to: 100, color: 'rgb(153,174,214)',
                        },
                        {
                            from: 101, to: 200, color: 'rgb(115,143,199)',
                        },
                        {
                            color: 'rgb(77,112,184)'
                        }]
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Hide desired legend items

To enable or disable the desired legend for each colormapping, set the `showLegend` property to `true` in `colorMapping`.

The following code example shows legends for the items excluded from color mapping.

Finally set `legendSettings.visible` as true and Inject the Legend Module into Maps using
`<Inject services={[Legend]}/>` tag.

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
                            from: 0, to: 100, color: 'rgb(153,174,214)',
                            showLegend: true
                        },
                        {
                            from: 101, to: 200, color: 'rgb(115,143,199)',
                            showLegend: false
                        },
                        {
                            color: 'rgb(77,112,184)', showLegend: false
                        }]
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Hide legend items based data source value

To enable or disable the legend visibility for each item, bind the field name in the data source to the `showLegendPath` property in `legendSettings`.

The following code example shows how to hide the legend items based data source value.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { dafaultData } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" legendSettings={ { visible: true , showLegendPath: 'visibility'} } >
            <Inject services={[Legend]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='continent' shapePropertyPath='continent' dataSource={dafaultData}
                        shapeSettings={ {
                            colorValuePath: 'color',
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Bind legend item text from data source

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

The following code example shows how to hide the legend items based data source value.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { dafaultData } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" legendSettings={ { visible: true , valuePath: 'continent'} } >
            <Inject services={[Legend]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='continent' shapePropertyPath='continent' dataSource={dafaultData}
                        shapeSettings={ {
                            colorValuePath: 'color',
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Hide duplicate legend items

To show the legend text based on binding, the field name in the datasource should be set to the `valuePath` property in `legendSettings`.

The following code example shows how to hide the legend items based data source value.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { dafaultData } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" legendSettings={ { visible: true , valuePath: 'continent' ,
            removeDuplicateLegend: true} } >
            <Inject services={[Legend]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='continent' shapePropertyPath='continent' dataSource={dafaultData}
                        shapeSettings={ {
                            colorValuePath: 'color',
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Toggle option in legend

The toggle option has been provided for legend. So, if you toggle a legend, the given color will be changed to the corresponding maps shape item. You can enable the toggle options using the `toggleLegendSettings` property.

The following options are available to customize the shape of the map:

* applyShapeSettings – Applies the fill property value in `shapeSettings` to a shape of the maps if it                         is true and a legend item is clicked.

* fill- Specifies the color to the shape of the maps.

* opacity – Specifies the transparency of the legend.

* border – Specifies the border color and width.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import { population_density } from 'data.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, Legend } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" legendSettings={ { visible: true, toggleLegendSettings: { enable: true } } } >
            <Inject services={[Legend]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} shapeDataPath='name' shapePropertyPath='name'
                        dataSource={population_density}
                        shapeSettings={ {
                            colorValuePath: 'density',
                            colorMapping: [
                                {
                                    from: 0, to: 100, color: 'rgb(153,174,214)',
                                },
                                {
                                    from: 101, to: 200, color: 'rgb(115,143,199)',
                                },
                                {
                                    color: 'rgb(77,112,184)'
                                }
                            ]
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

Refer the [`API`](../api/maps/legendSettingsModel/) for Legend feature.