# Drilldown

By clicking a continent, you can view all the countries available in that continent using the drill-down
feature. For example, the countries in the `Africa` continent have been showcased here. You can showcase
all the countries in `Africa` continent by clicking the [shapeSelected](../../api/maps/#shapeselected)
event as mentioned in the following code example.

{% tab compileJsx=true%}

```tsx
import { World_Map } from './MapData/WorldMap';
import { Africa } from './MapData/Africa';
import { dafaultData } from './MapData/salesCountry';
import * as React from 'react';
import './App.css';
import {
  MapsComponent, LayersDirective, LayerDirective, Inject,
  Highlight, IShapeSelectedEventArgs, Marker, MarkerDirective, MarkersDirective
} from '@syncfusion/ej2-react-maps';
//tslint:disable
interface ShapeData {
  continent?: string;
}
class App extends React.Component {
  private mapInstance: MapsComponent;
  private shapeSelected(args: IShapeSelectedEventArgs) {
    let shape = (args.shapeData as ShapeData).continent;
    if (this.mapInstance.baseLayerIndex === 0) {
      if (shape === 'Africa') {
        this.mapInstance.baseLayerIndex = 1;
        this.mapInstance.refresh();
      }
    }
  }
  render() {
    return (
      <MapsComponent id="element" height='400' ref={m => this.mapInstance = m as MapsComponent} shapeSelected={this.shapeSelected.bind(this)} >
        <Inject services={[Highlight, Marker]} />
        <LayersDirective>
          <LayerDirective shapeData={World_Map} layerType='Geometry' shapeDataPath='continent' shapePropertyPath='continent' dataSource={dafaultData} shapeSettings={{
            colorValuePath: 'drillColor'
          }}>
            <MarkersDirective>
              <MarkerDirective visible={true} template='<div style="font-size: 12px;color:white;text-shadow: 0px 1px 1px black;font-weight: 500;width:50px">Africa</div>' dataSource={
                [{ latitude: 10.97274101999902, longitude: 16.390625 }]
              } animationDuration={0} >
              </MarkerDirective>
            </MarkersDirective>
          </LayerDirective>
          <LayerDirective layerType='Geometry' shapeData={Africa} shapeSettings={{
            fill: '#80306A'
          }} highlightSettings={{
            enable: true,
            fill: '#80306A'
          }} >
          </LayerDirective>
        </LayersDirective>
      </MapsComponent>);
  }
}
export default App;
```

{% endtab %}