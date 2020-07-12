# Customization

## customizing shape

The following properties are available in `shapeSettings` property to customize the shapes of the Maps component.

* `fill` - Customizes the shape color.
* `autofill` - Applies the default palette colors to shapes.
* `palette` - Applies own custom palette for shapes.
* `border` - Customizes the maps shape border.
* `dashArray` - Customizes the different dash array border line format.
* `opacity` - Customizes the shape opacity.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                        shapeSettings={ {
                            fill: '#33CCFF',
                            border: { color: '#FFFFFF', width: 2}
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

 {% endtab %}

To apply the default palette colors to shapes, enable the `autofill` property.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
ReactDOM.render(
            <MapsComponent id="element">
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                        shapeSettings={ {
                            autofill: true
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

To apply own custom palette to shape, provide the palette colors to `palette`.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
ReactDOM.render(
            <MapsComponent id="element">
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                        shapeSettings={ {
                            autofill: true,
                            palette: ['#33CCFF', '#FF0000', '#800000', '#FFFF00', '#808000']
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

Refer the `shapeSettings` [`API`](../api/maps/shapeSettingsModel/) for Shape Customization.
For more customization see [`colormapping`](./color-mapping/) feature.

## Projection Type

By default, the maps are rendered by Mercator projection type. In this type, the maps are rendered based on coordinates, so it is not stretched.

The maps control has the following projection types:

* Mercator
* Equirectangular
* Miller
* Eckert3
* Eckert5
* Eckert6
* Winkel3
* AitOff

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
ReactDOM.render(
            <MapsComponent id="element" projectioType='Miller'>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                        shapeSettings={ {
                            autofill: true,
                            palette: ['#33CCFF', '#FF0000', '#800000', '#FFFF00', '#808000']
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
            document.getElementById("maps") as HTMLElement
);
```

{% endtab %}
