# Map Providers

Map control support map providers such as OpenStreetMap that can be added to any layers in maps.

## Open Street Map

`OpenStreetMap` is a map of the entire world. The OpenStreetMap allows you to view, edit and use geographical
data in a collaborative way from any place on the Earth.

### Enable OSM

You can enable this feature by setting the `layerType` property value as “OSM”.

{% tab compileJsx=true%}

``` tsx
import * as React from 'react';
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
import './App.css';
class App extends React.Component {
    render() {
        return (
            <MapsComponent id="element">
                <LayersDirective>
                    <LayerDirective layerType="OSM"
                        urlTemplate="http://a.tile.openstreetmap.org/level/tileX/tileY.png">
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>);
    }
}
export default App;
```

{% endtab %}

#### URL Template

The `urlTemplate` property determines the format of tile map. You can specify the template for the tile layer.

## Bing Map

Bing Map is a key feature in accessing the external geospatial imagery services for deep-zoom satellite view.

### Enable Bing Maps

You can enable this feature by defining the layerType as “bing”. To get the type of bing map as aerial, aerialwithlabel and road.

{% tab compileJsx=true%}

```tsx
import * as React from 'react';
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';
import './App.css';
class App extends React.Component {
    render() {
        return (
            <MapsComponent id="element">
                <LayersDirective>
                    <LayerDirective layerType="Bing" bingMapType="AerialWithLabel"
                    key="//Place your key"
                    >
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>);
    }
}
export default App;
```

{% endtab %}

#### Key

The bing Map key is provided as input to this key property. The Bing Map key can be obtained from [http://www.microsoft.com/maps/create-a-bing-maps-key.aspx](http://www.microsoft.com/maps/create-a-bing-maps-key.aspx).
