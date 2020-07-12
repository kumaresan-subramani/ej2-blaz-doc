# Display geometry shape in bing maps

Usually bing map displays the maps in satellite view in which you can't make changes as per your requirement. To over come this, you can add maps shape as sublayer over the bing map and you can customize it as per your requirement. Kindly follow the below steps to add geometry shapes as sublayer in bing maps.

**Step 1**:

To render the map control as bing map, please set the layerType as bing and also provide your bing map's key.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html" ,es5Template="bing" %}

```typescript

import { Maps } from '@syncfusion/ej2-maps';

let map: Maps = new Maps({
    layers: [
        {
            layerType: 'Bing',
            // Provide your bing map key here
            key: 'AuQazZ3PUo3p2_c2KPhqMku-iKvee5fKcRREIg46MENqVTM9dp2ZyTbrHJpR9esZ'
        }
    ]
});

map.appendTo("#container");

```

{% endtab %}

**Step 2**:

You can add geometry shape in bing map, using sublayer concept. First import the shape data and set the type as subLayer and also assign your shape data to API shapeData.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html" ,es5Template="bing-map" %}

```typescript

import { Maps } from '@syncfusion/ej2-maps';
import { Africa_Continent } from './Africa_Continent.ts';

let map: Maps = new Maps({
    layers: [
        {
            layerType: 'Bing',
            key: 'AuQazZ3PUo3p2_c2KPhqMku-iKvee5fKcRREIg46MENqVTM9dp2ZyTbrHJpR9esZ'
        },
        {
            layerType: 'Geometry',
            type: 'SubLayer',
            shapeData: Africa_Continent,
            shapeSettings: {
                fill: 'blue'
            }
        }
    ]
});

map.appendTo("#container");

```

{% endtab %}

Above code will render Africa continent as sublayer in bing map.