# Navigation Lines

Navigation lines are used to denote the path between the two locations. We can use this feature as flight or train or sea routes.

## Customization

You can customize the following properties in the navigation lines by modifying their default values in `navigationlineSettings`

* Color - Specifies the color of navigation line.
* Dash array - Specifies the type of dash array line.
* Width - Specifies the line width.
* Angle - Specifies the navigation line angle.
* Highlight settings - Customizes the opacity, border, and fill color when the cursor hovers over it.
* Selection settings - Customizes the opacity, border, and fill color when the line is selected.

Following example shows rendering the path between two locations using latitudes and longitudes.

Yon can customize the navigation line color, dashArray, width and angle by modifying their default values in
`navigationLineSettings`.

Refer the below code snippet to navigate line between two cities in World map.
Import worldMap geo json data from WorldMap.ts file.
Import the `NavigationLine` Module and Inject into the Maps using `<Inject services={[NavigationLine]} />` tag.
Provide two locations latitude and longitude values to `navigationLineSettings`.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, NavigationLine, NavigationLinesDirective, NavigationLineDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="element">
                <Inject services={[NavigationLine]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                        <NavigationLinesDirective>
                            <NavigationLineDirective visible={true} latitude={[37.6276571, -122.4276688]}
                                longitude={[-74.0060, -117.7418381]} color="black" angle={90} width={2} dashArray="4"/>
                        </NavigationLinesDirective>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

## Enabling the arrows

You can enable the arrows in the navigation line using [`arrowSettings.showArrow`](../api/maps/arrow) API, also you can customize following properties in arrow

* color - Specifies the color of the arrow
* offset - Specifies the arrow's offset position
* position - Specifies the arrow position to `start` or `end` line
* size - Specifies the arrow size in pixel

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, NavigationLine, NavigationLinesDirective, NavigationLineDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="element">
                <Inject services={[NavigationLine]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                        <NavigationLinesDirective>
                            <NavigationLineDirective visible={true} latitude={[37.6276571, -122.4276688]}
                                longitude={[-74.0060, -117.7418381]} color="black" angle={90} width={2} dashArray="4" arrowSettings={{showArrow: true, size: 15, position: 'Start', }}/>
                        </NavigationLinesDirective>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}

Refer the [`API`](../api/maps/navigationLineSettingsModel/) for Navigation Lines feature.