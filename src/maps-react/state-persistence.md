# State Persistence

## State Persistence

State persistence allows the Maps to retain the current modal value in the browser cookies for state maintenance. This action is handled through the `enablePersistence` property which is set to false by default. When it is set to true, some of the Maps component model values will be retained even after refreshing the page.

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" enablePersistence={true} zoomSettings={ { enable: true } }>
            <Inject services={[Zoom]}/>
                <LayersDirective>
                    <LayerDirective shapeData={world_map}>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```
