# Center position zooming

You can achieve the center position zooming by using the [centerPosition](../../api/maps/#centerposition)
and [zoomFactor](../../api/maps/zoomSettings/#zoomfactor) APIs as mentioned in the following code example. The
center position is used to configure the zoom level of maps, and zoom factor is used to specify the center
position where the map should be displayed.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import {
  MapsComponent, LayersDirective, LayerDirective,
  Inject, Zoom
} from '@syncfusion/ej2-react-maps';
//tslint:disable

ReactDOM.render(
      <MapsComponent id="maps" zoomSettings={{
        enable: false,
        zoomFactor: 13
      }} centerPosition={{
        latitude: 25.54244147012483,
        longitude: -89.62646484375
      }} >
        <Inject services={[Zoom]} />
        <LayersDirective>
          <LayerDirective shapeData={world_map}>
          </LayerDirective>
        </LayersDirective>
      </MapsComponent>,
       document.getElementById("maps") as HTMLElement
      );
```

{% endtab %}