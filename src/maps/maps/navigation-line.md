# Navigation Lines

Navigation lines are used to denote the path between the two locations. We can use this feature as flight or train or sea routes.

Following example shows rendering the path between two locations using latitudes and longitudes.

Yon can customize the navigation line color, dashArray, width and angle by modifying their default values in
`navigationLineSettings`.

Refer the below code snippet to navigate line between two cities in World map.
Import usmap geo json data from world_map.ts file.
Import the `NavigationLine` Module and Inject into the Maps using `Maps.Inject(NavigationLine)`.
Provide two locations latitude and longitude values to `navigationLineSettings`.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "navigation" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, NavigationLine } from '@syncfusion/ej2-maps';
Maps.Inject(NavigationLine);
let map: Maps = new Maps({
    layers: [{
        navigationLineSettings: [{
            visible: true,
            latitude: [40.7128, 36.7783],
            longitude: [-74.0060, -119.4179],
            color: 'black',
            angle: 90,
            width: 2,
            dashArray: '4'
        }],
        shapeData: world_map,
    }]
});
map.appendTo('#element');
```

{% endtab %}

Refer the [`API`](../api/maps/navigationLineSettingsModel/) for Navigation Lines feature.