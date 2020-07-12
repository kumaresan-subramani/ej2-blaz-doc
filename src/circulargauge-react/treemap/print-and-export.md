# Print and Export

## Print

To use the print functionality, we should inject the `Print` module into `services` and set the [`allowPrint`](../api/treemap/#allowprint) property to **true**. The rendered treemap can be printed directly from the browser by calling the method [`print`](../api/treemap/#print).

{% tab template= "treemap/printAndExport", compileJsx=true, sourceFiles="app/**/*.tsx", isDefaultActive=true %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, Print, Inject } from '@syncfusion/ej2-react-treemap';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';

export class App extends React.Component {
public click(){
  this.treemap.print();
}
private treemap: TreeMapComponent;
render() {
  return ( <div>
    <ButtonComponent value='Print' onClick= { this.click.bind(this)}>Print</ButtonComponent>
    <TreeMapComponent id='treemap' allowPrint={true} ref={g => this.treemap = g}
        dataSource={[
            {State:"United States", GDP:17946, percentage:11.08, Rank:1},
            {State:"China", GDP:10866, percentage: 28.42, Rank:2},
            {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
            {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
            {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
            {State:"France", GDP:2421, percentage:-9.69, Rank:6},
            {State:"India", GDP:2073, percentage:13.65, Rank:7},
            {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
            {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
            {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
        ]}
        weightValuePath= 'GDP'
        leafItemSettings= {{
            labelPath: 'State',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        }}>
        <Inject services={[Print]} />
    </TreeMapComponent></div> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module into `services` and set the [`allowImageExport`](../api/treemap/#allowimageexport) property to **true**. The rendered treemap can be exported as an image using the [`export`](../api/treemap/#export) method. The method requires two parameters: image type and file name. The treemap can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template= "treemap/printAndExport", compileJsx=true, sourceFiles="app/**/*.tsx" , isDefaultActive=true %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, ImageExport, Inject } from '@syncfusion/ej2-react-treemap';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';

export class App extends React.Component {
public click(){
  this.treemap.export('PNG', 'TreeMap');
}
public treemap: TreeMapComponent;
render() {
  return ( <div>
    <ButtonComponent value='Export' onClick= { this.click.bind(this)}>Export</ButtonComponent> <TreeMapComponent id='treemap' allowImageExport={true} ref={g => this.treemap = g}
        dataSource={[
            {State:"United States", GDP:17946, percentage:11.08, Rank:1},
            {State:"China", GDP:10866, percentage: 28.42, Rank:2},
            {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
            {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
            {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
            {State:"France", GDP:2421, percentage:-9.69, Rank:6},
            {State:"India", GDP:2073, percentage:13.65, Rank:7},
            {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
            {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
            {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
        ]}
        weightValuePath= 'GDP'
        leafItemSettings= {{
            labelPath: 'State',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        }}>
        <Inject services={[ImageExport]} />
    </TreeMapComponent> </div> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The treemap can be exported to image as a base64 string using the [`export`](../api/treemap/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template= "treemap/printAndExport", compileJsx=true, sourceFiles="app/**/*.tsx" , isDefaultActive=true %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, ImageExport, Inject } from '@syncfusion/ej2-react-treemap';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';

export class App extends React.Component {
public click(){
    this.treemap.export('PNG', 'TreeMap', null, false).then((data: string)=>{
        document.writeln(data);
    })
}
public treemap: TreeMapComponent;
render() {
  return ( <div>
    <ButtonComponent value='Export' onClick= { this.click.bind(this)}>Export</ButtonComponent> <TreeMapComponent id='treemap' allowImageExport={true} ref={g => this.treemap = g}
        dataSource={[
            {State:"United States", GDP:17946, percentage:11.08, Rank:1},
            {State:"China", GDP:10866, percentage: 28.42, Rank:2},
            {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
            {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
            {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
            {State:"France", GDP:2421, percentage:-9.69, Rank:6},
            {State:"India", GDP:2073, percentage:13.65, Rank:7},
            {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
            {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
            {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
        ]}
        weightValuePath= 'GDP'
        leafItemSettings= {{
            labelPath: 'State',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        }}>
        <Inject services={[ImageExport]} />
    </TreeMapComponent> </div> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module into `services` and set the [`allowPdfExport`](../api/treemap/#allowpdfexport) property to **true**. The rendered treemap can be exported as PDF using the [`export`](../api/treemap/#export) method. The [`export`](../api/treemap/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template= "treemap/printAndExport", compileJsx=true, sourceFiles="app/**/*.tsx" , isDefaultActive=true %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { TreeMapComponent, PdfExport, Inject } from '@syncfusion/ej2-react-treemap';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';

export class App extends React.Component {
public click(){
  this.treemap.export('PDF', 'export', 0);
}
public treemap: TreeMapComponent;
render() {
  return ( <div>
    <ButtonComponent value='Export' onClick= { this.click.bind(this)}>Export</ButtonComponent> <TreeMapComponent id='treemap' allowPdfExport={true} ref={g => this.treemap = g}
        dataSource={[
            {State:"United States", GDP:17946, percentage:11.08, Rank:1},
            {State:"China", GDP:10866, percentage: 28.42, Rank:2},
            {State:"Japan", GDP:4123, percentage:-30.78, Rank:3},
            {State:"Germany", GDP:3355, percentage:-5.19, Rank:4},
            {State:"United Kingdom", GDP:2848, percentage:8.28, Rank:5},
            {State:"France", GDP:2421, percentage:-9.69, Rank:6},
            {State:"India", GDP:2073, percentage:13.65, Rank:7},
            {State:"Italy", GDP:1814, percentage:-12.45, Rank:8},
            {State:"Brazil", GDP:1774, percentage:-27.88, Rank:9},
            {State:"Canada", GDP:1550, percentage:-15.02, Rank:10}
        ]}
        weightValuePath= 'GDP'
        leafItemSettings= {{
            labelPath: 'State',
            labelFormat: '${State}<br>$${GDP} Trillion<br>(${percentage} %)',
            labelStyle: {
                color: '#000000'
            },
            border: {
                color: '#000000',
                width: 0.5
            }
        }}>
        <Inject services={[PdfExport]} />
    </TreeMapComponent> </div> );
 }
}
ReactDOM.render(<App />, document.getElementById('treemap'));
```

{% endtab %}

>Note: The exporting of the treemap as base64 string is not supported in the PDF export.