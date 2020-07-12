# Multiple Layer

## Adding Multiple Layers in the Map

The multilayer support allows loading multiple shape files in a single container and enables maps to display more information.

Initialize the map component with SubLayer option by using the `type` property. The shape layer is the core
layer of the map. Multiple layers can be added in a shape layer as sublayers as mentioned in the following
code example. To know more about multiple layers, please refer to the [`API`](../../api/maps/layerSettings/)
documentation.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { usa_map } from 'usa.ts';
import { california } from 'california.ts';
import { texas } from 'texas.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
//tslint:disable
ReactDOM.render(
      <MapsComponent id="maps">
        <LayersDirective>
          <LayerDirective shapeData={usa_map} shapeSettings={
            {
              fill: '#E5E5E5',
              border: {
                color: 'black',
                width: 0.1
              }
            }
          } >
          </LayerDirective>
          <LayerDirective shapeData={texas} type='SubLayer' shapeSettings={
            {
              fill: 'rgba(141, 206, 255, 0.6)',
              border: {
                color: '#1a9cff',
                width: 0.25
              }
            }
          } >
          </LayerDirective>
          <LayerDirective shapeData={california} type='SubLayer' shapeSettings={
            {
              fill: 'rgba(141, 206, 255, 0.6)',
              border: {
                color: '#1a9cff',
                width: 0.25

              }
            }
          } >
          </LayerDirective>
        </LayersDirective>
      </MapsComponent>,
      document.getElementById("maps") as HTMLElement
      );
  ```

{% endtab %}