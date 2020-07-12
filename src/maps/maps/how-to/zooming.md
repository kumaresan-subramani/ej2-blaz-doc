# Center position zooming

You can achieve the center position zooming by using the [centerPosition](../../api/maps/centerPosition/) and [zoomFactor](../../api/maps/zoomSettings/#zoomfactor) APIs as mentioned in the following code example. The center position is used to configure the zoom level of maps, and zoom factor is used to specify the center position where the map should be displayed.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="position" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps,Zoom, ZoomSettings } from '@syncfusion/ej2-maps';
Maps.Inject(Zoom);

// initialize Maps component
let map: Maps = new Maps({
    zoomSettings:{
    enable:false,
    zoomFactor:13
    },
    centerPosition: {
        latitude: 25.54244147012483,
        longitude: -89.62646484375
    },
       layers: [
        {
            shapeData: world_map
        }
    ]
}, '#element');
```

{% endtab %}