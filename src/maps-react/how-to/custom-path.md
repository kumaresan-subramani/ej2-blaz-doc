# Custom Path Map

You can customize the maps control as the desired layout using the custom path map feature. Here, the maps
control has been showcased with normal geometry type shapes to represent the bus seat selection layout.
Please refer to the following code example to render the bus seat selection.

{% tab compileJsx=true%}

```tsx
import { seatData } from './MapData/seatSelection';
import * as React from 'react';
import './App.css';
import {
  MapsComponent, LayersDirective, LayerDirective,
  Inject, Selection
} from '@syncfusion/ej2-react-maps';
//tslint:disable
const bus_logo = require('./bus-icon.png');
const wheel_logo = require('./wheel.png');
class App extends React.Component {
  render() {
    return (
      <div className='control-section row'>
        <div className='col-md-8'>
          <div style={{ width: 200, margin: 'auto', paddingBottom: 20 }}>
            <img src={bus_logo} style={{ width: 25, height: 25, float: 'left' }}>
            </img>
            <div id="sampletitle">Bus seat selection</div>
          </div>
          <div style={{ border: '3px solid darkgray', width: 200, display: 'block', margin: 'auto' }}>
            <img src={wheel_logo} style={{ width: 30, height: 30, marginLeft: '18%', marginTop: 10 }}></img>
            <MapsComponent id="element" height='400'>
              <Inject services={[Selection]} />
              <LayersDirective>
                <LayerDirective shapeData={seatData} geometryType='Normal' selectionSettings={
                  {
                    enable: true,
                    opacity: 1,
                    enableMultiSelect: true
                  }
                } >
                </LayerDirective>
              </LayersDirective>
            </MapsComponent>
          </div></div></div>);
  }
}
export default App;
```

{% endtab %}