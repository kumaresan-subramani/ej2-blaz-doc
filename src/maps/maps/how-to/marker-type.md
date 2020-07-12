# Marker Types

## Add different types of markers

You can use different marker objects in maps control by using the marker settings.

To update different marker settings in maps, please follow the given steps:
<!-- markdownlint-disable MD034 -->
**Step 1**:

Initialize the maps control with marker settings. Here, a marker has been added with specified latitude and longitude of California by using the `dataSource` property. You can customize the shape of the marker using the `Shape` property and change the border color and width of the marker using the `border` property as mentioned in the following code example. To know more about the marker settings, please refer to the [`API`](../../api/maps/markerSettings/) documentation.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="step-one" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps , Marker, MarkerSettings } from '@syncfusion/ej2-maps';

// initialize Map component
let map: Maps = new Maps({
    //Initializing Map with Marker settings
  layers: [
        {
            shapeData: world_map,
            markerSettings: [
                {
                    dataSource: [
                       { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }
                    ],
                    visible:true,
                    shape:'Circle',
                    fill:'white',
                    width:3,
                    animationDuration:0,
                    border:{width:2,color:'#333'}
                }
            ]
        }
  ]
}, '#element');  // render initialized Map
```

{% endtab %}

**Step 2**:

Customize the above option for n number of markers as mentioned in the following code example.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template = "step-two" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps , Marker, MarkerSettings } from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
// initialize Maps component
let map: Maps = new Maps({
    layers: [
        {
            shapeData: world_map,
            markerSettings: [
                {
                    dataSource: [
                       { latitude: 37.6276571, longitude: -122.4276688, city: 'San Bruno' },
                    ],
                    visible:true,
                    shape:'Circle',
                    fill:'white',
                    width:3,
                    animationDuration:0,
                    border:{width:2,color:'#333'}
                },
                {
                    dataSource: [
                        { latitude: 33.5302186, longitude: -117.7418381, city: 'Laguna Niguel' },
                    ],
                    visible:true,
                    shape:'Rectangle',
                    fill:'yellow',
                    width:15,
                    height:4,
                    animationDuration:0,
                    border:{width:2,color:'#333'}
                },
                {
                    dataSource: [
                         { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }
                    ],
                    visible:true,
                    shape:'Diamond',
                    fill:'white',
                    width:10,
                    height:10,
                    animationDuration:0,
                    border:{width:2,color:'blue'}
                },
            ]
        }
    ]
}, '#element'); // render initialized Map
```

{% endtab %}

## Tooltip for marker

Tooltip is used to display more information about marker on mouse over or touch end event. This can be enabled separately for layer or marker by setting the `tooltipSettings.visible` property to **true**. The `valuePath` property in tooltip takes the field name that presents in dataSource and displays that value as tooltip text. The following code example illustrates enabling the tooltip for marker to show city name field. To know more about tooltip, please refer to the [`API`](../../api/maps/tooltipSettings/) documentation.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="marker-tooltip" %}

```typescript
import { usa_map } from './usa.ts';
import { Maps , Marker,MapsTooltip, MarkerSettings } from '@syncfusion/ej2-maps';
Maps.Inject(Marker,MapsTooltip);
// initialize Maps component
let map: Maps = new Maps({
    layers: [
        {
            shapeData: usa_map,
            markerSettings: [
                {
                    dataSource: [
                        { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }
                    ],
                    visible:true,
                    shape:'Circle',
                    fill:'white',
                    width:3,
                    animationDuration:0,
                    border:{width:2,color:'#333'},
                    tooltipSettings: {
                        visible: true,
                        valuePath:'city'
                }
                }
            ]
        }
    ],
    height: '450px',
    width: '700px'
}, '#element');
```

{% endtab %}