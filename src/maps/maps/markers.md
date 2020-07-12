# Markers

Markers are notes used to leave some message on the map.
There are two ways to set marker for map.

* Marker and marker template

* Adding marker objects to map.

## Marker and marker template

The `markerSettings.dataSource` property has a list of objects that contains the data for Annotation. By default, it displays the bound data at the specified latitude and longitude. The `markerSettings.template` property is used for customizing the template for markers.

**Note:** markerSettings is an Array property.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "marker" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        markerSettings: [
            {
                        visible: true,
                        template: '<div id="marker4" class="markerTemplate">Europe' +
                            '</div>',
                        dataSource: [
                            { latitude: 49.95121990866204, longitude: 18.468749999999998 }
                        ],
                        animationDuration: 0,
                    },
                    {
                        visible: true,
                        template: '<div id="marker5" class="markerTemplate" style="width:50px">North America' +
                            '</div>',
                        dataSource: [
                            { latitude: 59.88893689676585, longitude: -109.3359375 }
                        ],
                        animationDuration: 0
                    },
                    {
                        visible: true,
                        template: '<div id="marker6" class="markerTemplate" style="width:50px">South America' +
                            '</div>',
                        dataSource: [
                            { latitude: -6.64607562172573, longitude: -55.54687499999999 }
                        ],
                        animationDuration: 0
                    },

            }
        ]
    }]
});
map.appendTo('#element');
```

{% endtab %}

```html
<div  id="template" style="display: none;">
    <div>
        <div  style="background-image:url(http://js.syncfusion.com/demos/web/Images/map/pin.png)margin-left:3px;height:40px;width:25px;margin-top:-15px;">
        </div>
    </div>
</div>
```

## Adding marker objects to map

n number of markers can be added to shape layers with `markerSettings.dataSource` property. Each dataSource object contains the following list of properties.

label - Text that displays some information about the annotation in text format.
latitude - Latitude point determine the Y-axis position of annotation.
longitude - Longitude point determine the X-axis position of annotation.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "marker-object" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker} from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        markerSettings: [
            {
                visible: true,
                template: '<div> {{:city}}<div>',
                dataSource: [
                    { latitude: 37.0000, longitude: -120.0000, city: 'California' },
                    { latitude: 40.7127, longitude: -74.0059, city: 'New York' },
                    { latitude: 42, longitude: -93, city: 'Iowa' }
                ]
            }
        ]
    }]
});
map.appendTo('#element');
```

{% endtab %}

```html
<div  id="template" style="display: none;">
        <div>
            <div style="margin-left:8px;height:45px;width:120px;margin-top:-23px;">
                <label style="color:black;margin-left:15px;font-weight:normal;">\{\{\:city\}\}</label>
             </div>
         </div>
    </div>
```

## Enable the Legend for map markers

Legend can be enabled for marker using `legendSettings.type` as **Markers** and legend visible as true, need to inject Legend module to Maps using the `Maps.Inject(Legend)`. Refer the code snippet to enable the legend for the markers.

{% tab template= "maps/default-map",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "marker-object" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps, Marker, Legend} from '@syncfusion/ej2-maps';
Maps.Inject(Marker, Legend);
let map: Maps = new Maps({
    legendSettings: {
        visible: true,
        type: 'Markers'
    },
    layers: [{
        shapeData: world_map,
        markerSettings: [
            {
               visible: true,
               legendText: 'city',
                dataSource: [
                    { latitude: 37.0000, longitude: -120.0000, city: 'California' },
                    { latitude: 40.7127, longitude: -74.0059, city: 'New York' },
                    { latitude: 42, longitude: -93, city: 'Iowa' }
                ]
            }
        ]
    }]
});
map.appendTo('#element');
```

{% endtab %}

Refer the [`API`](../api/maps/markerSettingsModel/) for Marker feature.

## See Also

* [Add different types of markers](../maps/how-to/marker-type)
* [Tooltip for marker](../maps/how-to/marker-type)