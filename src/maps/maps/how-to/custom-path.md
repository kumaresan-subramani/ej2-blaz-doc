# Custom path map

You can customize the maps control as the desired layout using the custom path map feature. Here, the maps control has been showcased with normal geometry type shapes to represent the bus seat selection layout. Please refer to the following code example to render the bus seat selection.
<!-- markdownlint-disable MD031 -->
{% tab template= "maps/how-to/custom-path", es5Template="custom-path" %}

```typescript
import { seat } from './seat.ts';
import { Maps,Selection } from '@syncfusion/ej2-maps';
Maps.Inject(Selection);
// initialize Maps component
let map: Maps = new Maps({
        layers: [
        {
            geometryType: 'Normal',
            shapeData: seat,
            selectionSettings: {
                enable: true,
                opacity: 1,
                enableMultiSelect: true
            }
        }
    ],
    height: '400'
}, '#container');

```
{% endtab %}

```html
 <div class="col-lg-9 control-section">
      <div style="width:200px;margin:auto;padding-bottom:20px">
          <img src="src/app/images/bus-icon.png" style="width:25px;height:25px;float:left">
          <div style="padding-left:30px;font-size:20px;font-weight:400;">Bus seat selection</div>
      </div>
      <div style="border: 3px solid darkgray;width:200px;display:block;margin:auto;border-radius:5px">
          <img src="src/app/images/wheel.png" style="width:30px;height:30px;margin-left:18%;margin-top:10px">
          <div id="maps"></div>
      </div>
  </div>
```