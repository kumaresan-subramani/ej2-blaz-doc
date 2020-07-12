# Print and Export

## Print

To use the print functionality, we should inject the `Print` module into `services` and set the [`allowPrint`](../api/maps/#allowprint) property to **true**. The rendered map can be printed directly from the browser by calling the method [`print`](../api/maps/#print).

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { MapsComponent, LayersDirective, LayerDirective, Inject, Print, DataLabel } from '@syncfusion/ej2-react-maps';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.maps.print();
}
private maps: MapsComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>print</ButtonComponent>
            <MapsComponent id="maps" allowPrint={true} ref={g => this.maps = g}>
                <Inject services={[DataLabel, Print]} />
                <LayersDirective>
                    <LayerDirective shapeData={world_map}
                     dataLabelSettings={ {
                            visible: true,
                            labelPath: 'name',
                            smartLabelMode: 'Trim'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('maps'));

```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module into `services` and set the [`allowImageExport`](../api/maps/#allowimageexport) property to **true**. The rendered map can be exported as an image using the [`export`](../api/maps/#export) method. The method requires two parameters: image type and file name. The map can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { usa_map } from 'usa.ts';
import { election_data } from 'data.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { MapsComponent, LayersDirective, LayerDirective, MapsTooltip, Inject, ImageExport } from '@syncfusion/ej2-react-maps';
import {Legend, } from '@syncfusion/ej2-react-maps';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');

class App extends React.Component<{}, {}>{
public clickHandler(){
  this.maps.export('PNG', 'Maps');
}
private maps: MapsComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
            <MapsComponent id="maps" allowImageExport={true} ref={g => this.maps = g} format='c' legendSettings={ { visible: true } }
                titleSettings={ { text: 'USA Election Results - 2016' } }>
                <Inject services={[Legend, MapsTooltip, ImageExport]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map} shapeDataPath='State' shapePropertyPath='name' dataSource={election_data}
                        shapeSettings={ {
                            colorValuePath: 'Candidate',
                            colorMapping: [
                                { value: 'Trump', color: '#D84444' },
                                { value: 'Clinton', color: '#316DB5' }
                            ]
                        } }
                        tooltipSettings={ {
                            visible: true,
                            valuePath: 'value'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('maps'));
```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The rendered map can be exported to image as a base64 string using the [`export`](../api/maps/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { usa_map } from 'usa.ts';
import { election_data } from 'data.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { MapsComponent, LayersDirective, LayerDirective, MapsTooltip, Inject, ImageExport } from '@syncfusion/ej2-react-maps';
import {Legend, } from '@syncfusion/ej2-react-maps';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');

class App extends React.Component<{}, {}>{
public clickHandler(){
    this.maps.export('PNG', 'Maps', null, false).then((data: string)=>{
        document.writeln(data);
    })
}
private maps: MapsComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
            <MapsComponent id="maps" allowImageExport={true} ref={g => this.maps = g} format='c' legendSettings={ { visible: true } }
                titleSettings={ { text: 'USA Election Results - 2016' } }>
                <Inject services={[Legend, MapsTooltip, ImageExport]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map} shapeDataPath='State' shapePropertyPath='name' dataSource={election_data}
                        shapeSettings={ {
                            colorValuePath: 'Candidate',
                            colorMapping: [
                                { value: 'Trump', color: '#D84444' },
                                { value: 'Clinton', color: '#316DB5' }
                            ]
                        } }
                        tooltipSettings={ {
                            visible: true,
                            valuePath: 'value'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('maps'));
```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module into `services` and set the [`allowPdfExport`](../api/maps/#allowpdfexport) property to **true**. The rendered map can be exported as PDF using the [`export`](../api/maps/#export) method. The [`export`](../api/maps/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { usa_map } from 'usa.ts';
import { election_data } from 'data.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { MapsComponent, LayersDirective, LayerDirective, MapsTooltip, Inject, PdfExport } from '@syncfusion/ej2-react-maps';
import {Legend, } from '@syncfusion/ej2-react-maps';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');

class App extends React.Component<{}, {}>{
public clickHandler(){
  this.maps.export('PDF', 'Maps', 0);
}
private maps: MapsComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
            <MapsComponent id="maps" allowPdfExport={true} ref={g => this.maps = g} format='c' legendSettings={ { visible: true } }
                titleSettings={ { text: 'USA Election Results - 2016' } }>
                <Inject services={[Legend, MapsTooltip, PdfExport]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map} shapeDataPath='State' shapePropertyPath='name' dataSource={election_data}
                        shapeSettings={ {
                            colorValuePath: 'Candidate',
                            colorMapping: [
                                { value: 'Trump', color: '#D84444' },
                                { value: 'Clinton', color: '#316DB5' }
                            ]
                        } }
                        tooltipSettings={ {
                            visible: true,
                            valuePath: 'value'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('maps'));
```

{% endtab %}

>Note: The exporting of the map as base64 string is not supported in the PDF export.

### Export the tile maps

The rendered map with providers such as OSM, Bing and Google static maps can be exported using the [`export`](../api/maps/#export) method. It supports the following export formats.

* JPEG
* PNG
* PDF

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { usa_map } from 'usa.ts';
import { election_data } from 'data.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { MapsComponent, LayersDirective, LayerDirective, MapsTooltip, Inject, ImageExport, PdfExport } from '@syncfusion/ej2-react-maps';
import {Legend, } from '@syncfusion/ej2-react-maps';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');

class App extends React.Component<{}, {}>{
public clickHandler(){
  this.maps.export('PNG', 'Maps');
}
private maps: MapsComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
            <MapsComponent id="maps" allowPdfExport={true} allowImageExport={true} ref={g => this.maps = g} format='c' legendSettings={ { visible: true } }
                titleSettings={ { text: 'OSM' } }>
                <Inject services={[Legend, MapsTooltip, ImageExport, PdfExport]} />
                <LayersDirective>
                    <LayerDirective layerType='OSM'>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('maps'));
```

{% endtab %}