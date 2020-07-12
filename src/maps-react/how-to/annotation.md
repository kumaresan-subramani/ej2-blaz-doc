# Annotations

Annotations are used to mark the specific area of interest in a map area with texts, shapes, or images. To
update the annotation in maps, please follow the given procedure.

Initialize the maps control with annotation option, and specify the ID of HTML element in the content that
needs to be displayed in maps area by using the `content` property. You can specify the content position
with `x` and `y` values as mentioned in the following code example. To know more about annotations, please
refer to the [`API`](../../api/maps/annotation/) documentation.

In annotation, you can import the image in the specified map area by using require function as mentioned in the below code example.

```sh
const logo = require('./compass.png');
<img src={logo} height="75px" width="75px"/>
```

[`app.tsx`]

{% tab compileJsx=true%}

```tsx
import { africa_continent } from './MapData/africa_continent';
import * as React from 'react';
import './App.css';
import {
  MapsComponent, LayersDirective, LayerDirective, Inject,
  Annotations
} from '@syncfusion/ej2-react-maps';
//tslint:disable
const SAMPLE_CSS = `
    .control-fluid {
    padding: 0px !important;
    }
    #annotation {
        color: #DDDDDD;
        font-size: 12px;
        font-family: Roboto;
        background: #3E464C;
        margin: 20px;
        padding: 10px;
        -webkit-border-radius: 2px;
        -moz-border-radius: 2px;
        border-radius: 2px;
        width: 300px;
        -moz-box-shadow: 0px 2px 5px #666;
        -webkit-box-shadow: 0px 2px 5px #666;
        box-shadow: 0px 2px 5px #666;
    }`;
const logo = require('./compass.png');
class App extends React.Component {
  render() {
    return (
      <div className='control-pane'>
        <style>
          {SAMPLE_CSS}
        </style>
        <div className='control-section row'>
          <MapsComponent id="element" annotations={[
            {
              content: '#maps-annotation',
              x: '0%', y: '70%'
            }, {
              content: '#compass-maps',
              x: '85%', y: '5%'
            }
          ]} >
            <Inject services={[Annotations]} />
            <LayersDirective>
              <LayerDirective shapeData={africa_continent}>
              </LayerDirective>
            </LayersDirective>
          </MapsComponent>
        </div>
        <svg height="150" width="400">
          <defs>
            <linearGradient id="grad1" x1="0%" y1="0%" x2="0%" y2="100%">
              <stop offset="0%" style={
                { stopColor: '#C5494B', stopOpacity: '1' }
                } />
              <stop offset="100%" style={
                { stopColor: '#4C134F', stopOpacity: '1' }
                } />
            </linearGradient>
          </defs>
        </svg>
        <div id="maps-annotation" style={
          { display: 'none' }
          }>
          <div id="annotation">
            <div style={
              { marginLeft: '10px', fontsize: '13px', fontweight: 500 }
              }>
              <h5 style={
                { marginLeft: '40px' }
                }>Facts about Africa</h5>
            </div>
            <hr />
            <div>
              <ul style={
                { listStyleType: 'disc' }
                }>
                <li>Africa is the second largest and second most populated continent in the world.</li>
                <li style={
                  { paddingtop: '5px' }
                  }>Africa has 54 sovereign states and 10 non-sovereign territories.</li>
                <li style={
                  { paddingtop: '5px' }
                  }>Algeria is the largest country in Africa, where as Mayotte is the smallest.</li>
              </ul>
            </div>
          </div>
        </div>
        <div id="compass-maps" style={
          { display: 'none' }
          }>
          <img src={logo} height="75px" width="75px" />
        </div>
      </div>);
  }
}
export default App;
```

{% endtab %}