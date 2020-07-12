
# User Interactions

Options like zooming, panning, single click and double click, highlight and map selection enables the effective interaction on Map elements.

## Zooming

The zooming feature enables you to zoom in and out the Map to show in-depth information. It is controlled by
the `zoomFactor` property of the `zoomSettings` of the map. When the zoomFactor is increased, the Map is
zoomed in. When the zoomFactor is decreased, then the Map is zoomed out.

### Enable Zooming

To enable the zooming feature, set the `zoomSettings.enable` as true in maps. Zooming feature needs the `Zoom`
module injection to perform zooming actions, use module injection to inject zoom into Maps by using `<Inject services={[Zoom]}/>` tag.

### Enable panning

To enable the panning feature, set the [`enablePanning`](../api/maps/zoomSettings/#enablepanning) property of [`zoomSettings`](../api/maps/zoomSettings) to **true**.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true, enablePanning: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

### Various type of zooming

Zooming can be performed by various types. click zooming, double click zooming, toolbar zooming
rectangular zooming, mouse wheel zooming and pinch zooming.

<b>Zooming toolbar</b>

By default, the toolbar is rendered with `zoom-in`, `zoom-out`, and `reset` options when it is set to 'true' in the `enable` property of `zoomSettings`. You can also customize the toolbar items using the `toolBArs` property in `zoomSettings`.

The following options are available in toolbar, and you can use the options as needed:

1. Zoom - Provides rectangular zoom support.
2. ZoomIn - Zooms in the maps.
3. ZoomOut - Zooms out the maps.
4. Pan - Switches to panning if rectangular zoom is activated.
5. Reset - Restores the maps to the default view.

Refer the [`API`](../api/maps/zoomSettingsModel/) links for Zooming.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

<b>Pinch Zooming</b>

Use the `pinchZooming` property in `zoomSettings` to enable or disable the pinch zooming.

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true pinchZooming: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

<b>Single-click zooming</b>

Use the `zoomOnClick` property in `zoomSettings` to enable or disable the single-click zooming

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true zoomOnClick: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

<b>Double-click zooming</b>

Use the `doubleClickZoom` property in `zoomSettings` to enable or disable the double-click zooming.

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true doubleClickZoom: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

<b>Mouse wheel zooming</b>

Use the `mouseWheelZoom` property in `zoomSettings` to enable or disable mouse wheel zooming.

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true mouseWheelZoom: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

### Zooming with animation

You can use the `animationDuration` property in  `layers` property to zoom in or zoom out the maps with animation.

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings={ { enable: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map} animationDuration={500}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

## Selection

Each shape in the Map can be selected and deselected during interaction with the shapes.

By tapping on the specific legend, the shapes which are bounded to the selected legend is also selected and vice versa.

The layer `selectionSettings.fill` property is used to change the selected layer shape color. The
`selectionSettings.border.color` and `selectionSettings.border.width` properties are used to customize the selected shape border.

You can select the shape by tapping the shape. The Single selection is enabled by the
`selectionSettings.enable` property of shape layer. When `selectionSettings.enable` is set to false, the shapes cannot be selected.

Refer the [`API`](../api/maps/selectionSettingsModel/) and code snippet for Selection.

**Note:** Selection is separate module, need to inject to work on Selection.`<Inject services={[Selection]} />`

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Selection, Inject  } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[Selection]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} selectionSettings={ {
                        enable: true,
                        fill: 'green',
                        border: { color: 'white', width: 2 }
                    } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Public method for the shape selection

Each shape in the map can be selected by calling the `shapeSelection` method. Input parameters for this method are layerIndex, propertyName, country name and selected value as in boolean state(true / false).

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Selection, Inject } from '@syncfusion/ej2-react-maps';

class App extends React.Component<{}, {}>{

  public mapsInstance: MapsComponent;
  public selectclickHandler() {
    this.mapsInstance.shapeSelection(0, "continent", "Asia", true);
  }
  public unselectclickHandler() {
    this.mapsInstance.shapeSelection(0, "continent", "Asia", false);
  }
  render() {
    return (<div>
      <MapsComponent id="maps" ref={maps => this.mapsInstance = maps}>
            <Inject services={[Selection]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map} selectionSettings={ {
                        enable: true,
                        fill: 'green',
                        border: { color: 'white', width: 2 }
                    } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>
            <button value='select' onClick={this.selectclickHandler.bind(this)}>select</button>
            <button value='unselect' onClick={this.unselectclickHandler.bind(this)}>unselect</button></div>)
  }
};
ReactDOM.render(<App />, document.getElementById('maps'));

```

{% endtab %}

## Initial shape selection

Initially, the shape can be selected by using the property `initialShapeSelection` and the values are mapped to the `shapePath` and `shapeValue`.

**Note:** initialShapeSelection is an Array property.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, initialShapeSelectionsDirective, initialShapeSelectionDirective, LayerDirective, Selection, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[Selection]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}  selectionSettings={ {
                        enable: true,
                        fill: 'green',
                        border: { color: 'white', width: 2 }
                    } }>
            <initialShapeSelectionsDirective>
                <initialShapeSelectionDirective shapePath= {'continent'} shapeValue= {'Africa'}>
                </initialShapeSelectionDirective>
                <initialShapeSelectionDirective shapePath= {'name'} shapeValue= {'India'} >
                </initialShapeSelectionDirective>
            </initialShapeSelectionsDirective>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Highlight

Each shape in the Map can be highlighted during mouse over on the shapes.

Hovering on the specific legend, the shapes which are bounded to the selected legend is also highlighted and vice versa.

The layer `highlightSettings.fill` property is used to change the highlighted layer shape color. The
`highlightSettings.border.color` and `highlightSettings.border.width` properties are used to customize the highlighted shape border.

You can highlight the shape by mouse over on the shape. The highlight is enabled by the
`highlightSettings.enable` property of shape layer. When `highlightSettings.enable` is set to false, the shapes cannot be highlighted.

**Note:** Highlight is separate module, need to inject to work on Highlight.
`<Inject services={[Highlight]} />`

Refer the [`API`](../api/maps/highlightSettingsModel/) and code snippet for Highlight.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Highlight, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[Highlight]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}  highlightSettings={ {
                        enable: true,
                        fill: 'green',
                        border: { color: 'white', width: 2 }
                    } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Tooltip

Tooltip used to get more information about layer or bubble or marker on mouse over or touch end event
performing on that. Tooltip is a separate module, So it needs module injection to work maps tooltip. Using
`<Inject services={[MapsTooltip]} />` tag you can inject maps tooltip module into maps.

Tooltip can be enabled separately for layer or bubble or marker by using `tooltipSettings.visible` as
**true**. Tooltip `valuePath` value need to set to display dataSource which field as tooltip text.
Below code snippet illustrate the tooltip enabled for layer to show shape data name field.

Refer the [`API`](../api/maps/tooltipSettingsModel/) for Tooltip feature.

**Step: 1** Import the usmap geo json data from already created worldMap.ts file and assign to `shapeData`.

**Step: 2** Import MapsTooltip module from `ej2-maps` package and Inject to Maps.

**Step: 3** Enable tooltip for layer using `tooltipSettings.visible` as true and bind `valuePath` value as 'name'.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MapsTooltip, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                        <Inject services={[MapsTooltip]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}  tooltipSettings={ {
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
