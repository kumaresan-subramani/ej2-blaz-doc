# Marker Type

## Add different types of markers

You can use different marker objects in maps control by using the marker settings.

To update different marker settings in maps, please follow the given steps:

**Step 1**:

Initialize the maps control with marker settings. Here, a marker has been added with specified latitude and
longitude of California by using the `dataSource` property. You can customize the shape of the marker using
the `Shape` property and change the border color and width of the marker using the `border` property as
mentioned in the following code example. To know more about the marker settings, please refer to the
[`API`](../../api/maps/markerSettings/) documentation.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import {
  MapsComponent, LayersDirective, LayerDirective, MarkersDirective,
  MarkerDirective, Inject, Marker
} from '@syncfusion/ej2-react-maps';
ReactDOM.render(
      <MapsComponent id="element">
        <Inject services={[Marker]} />
        <LayersDirective>
          <LayerDirective shapeData={usa_map}>
            <MarkersDirective>
              <MarkerDirective visible={true} shape='Circle' fill='white' width={3} animationDuration={0}
                dataSource={[
                  { latitude: 37.0000, longitude: -120.0000, city: 'California' }
                ]}
                border={{ width: 2, color: '#333' }}>
              </MarkerDirective>
            </MarkersDirective>
          </LayerDirective>
        </LayersDirective>
      </MapsComponent>,
       document.getElementById("maps") as HTMLElement
      );
```

{% endtab %}

**Step 2**:

Customize the above option for n number of markers as mentioned in the following code example.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import {
  MapsComponent, LayersDirective, LayerDirective, MarkersDirective,
  MarkerDirective, Inject, Marker
} from '@syncfusion/ej2-react-maps';
//tslint disable
ReactDOM.render(
      <MapsComponent id="maps">
        <Inject services={[Marker]} />
        <LayersDirective>
          <LayerDirective shapeData={usa_map}>
            <MarkersDirective>
              <MarkerDirective visible={true} shape='Circle' fill='white' width={3} animationDuration={0}
                dataSource={[
                  { latitude: 37.0000, longitude: -120.0000, city: 'California' }
                ]}
                border={
                  { width: 2, color: '#333' }
                  }>
                </MarkerDirective>
              <MarkerDirective visible={true} shape='Rectangle' fill='yellow' width={15} height={4} animationDuration={0}
                dataSource={[
                  { latitude: 40.7127, longitude: -74.0059, city: 'New York' }
                ]}
                border={
                  { width: 2, color: '#333' }
                  }>
                </MarkerDirective>
              <MarkerDirective visible={true} shape='Diamond' fill='white' width={10} height={10} animationDuration={0}
                dataSource={[
                  { latitude: 42, longitude: -93, city: 'Iowa' }
                ]}
                border={
                  { width: 2, color: 'blue' }
                  }>
                </MarkerDirective>
              <MarkerDirective visible={true} shape='Balloon' fill='red' width={10} height={15} animationDuration={0}
                dataSource={[
                  { latitude: 36.499589049395055, longitude: -103.042108197135548, city: 'New Mexico' }
                ]}
                border={
                  { width: 2, color: '#333' }
                  }>
                </MarkerDirective>
              <MarkerDirective visible={true} shape='Triangle' fill='blue' width={10} animationDuration={0}
                dataSource={[
                  { latitude: 36.360624205142919, longitude: -94.595916790727287, city: 'Oklahoma' }
                ]}
                border={
                  { width: 2, color: '#333' }
                  }>
                </MarkerDirective>
            </MarkersDirective>
          </LayerDirective>
        </LayersDirective>
      </MapsComponent>,
      document.getElementById("maps") as HTMLElement
      );
```

{% endtab %}

## Tooltip for Marker

Tooltip is used to display more information about marker on mouse over or touch end event. This can be
enabled separately for layer or marker by setting the `tooltipSettings.visible` property to **true**. The
`valuePath` property in tooltip takes the field name that presents in dataSource and displays that value as
tooltip text. The following code example illustrates enabling the tooltip for marker to show city name
field. To know more about tooltip, please refer to the [`API`](../../api-tooltipSettings.html) documentation.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import * as React from 'react';
import {
  MapsComponent, LayersDirective, LayerDirective, MarkersDirective, MarkerDirective,
  Marker, MapsTooltip, Inject
} from '@syncfusion/ej2-react-maps';
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";

//tslint:disable
ReactDOM.render(
      <MapsComponent id="maps" height='450px' width='700px'>
        <Inject services={[Marker, MapsTooltip]} />
        <LayersDirective>
          <LayerDirective shapeData={usa_map}>
            <MarkersDirective>
              <MarkerDirective visible={true} shape='Circle' fill='white' width={3} animationDuration={3} dataSource={[
                { latitude: 37.0000, longitude: -120.0000, city: 'California' }
              ]} border={{
                width: 2, color: '#333'
              }
              } tooltipSettings={
                {
                  visible: true, valuePath: 'city'
                }
              } >
              </MarkerDirective>
            </MarkersDirective>
          </LayerDirective>
        </LayersDirective>
      </MapsComponent>,
      document.getElementById("maps") as HTMLElement
    );
```

{% endtab %}