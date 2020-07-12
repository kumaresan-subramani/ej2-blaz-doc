# Print and Export

## Print

To use the print functionality, we should inject the `Print` module into `services` and set the [`allowPrint`](../api/circular-gauge/#allowprint) property to **true**. The rendered circular gauge can be printed directly from the browser by calling the method [`print`](../api/circular-gauge/#print).

{% tab template="circulargauge/gauge-print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CircularGaugeComponent, AxesDirective, Print, Inject, AxisDirective, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.circular.print();
}
private circular: CircularGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='print' onClick= { this.clickHandler.bind(this)}>print</ButtonComponent>
        <CircularGaugeComponent id='circulargauge' allowPrint={true} ref={g => this.circulargauge = g}>
        <Inject services={[Print]} />
        </CircularGaugeComponent>
        </div>)
        }
};
ReactDOM.render(<App />, document.getElementById('circulargauge'));

```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module into `services` and set the [`allowImageExport`](../api/circular-gauge/#allowimageexport) property to **true**. The rendered circular gauge can be exported as an image using the [`export`](../api/circular-gauge/#export) method. The method requires two parameters: image type and file name. The circular gauge can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template="circulargauge/gauge-print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CircularGaugeComponent, AxesDirective, AxisDirective, ImageExport, Inject, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.circular.export('PNG','Gauge');
}
private circular: CircularGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
        <CircularGaugeComponent id='circulargauge' allowImageExport={true} ref={g => this.circulargauge = g}>
            <Inject services={[ImageExport]} />
        </CircularGaugeComponent>
        </div>)
        }
};
ReactDOM.render(<App />, document.getElementById('circulargauge'));

```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The circular gauge can be exported to image as a base64 string using the [`export`](../api/circular-gauge/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template="circulargauge/gauge-print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CircularGaugeComponent, AxesDirective, AxisDirective, ImageExport, Inject, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
    this.circular.export('PNG', 'Gauge', null, false).then((data: string)=>{
        document.writeln(data);
    })
}
private circular: CircularGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
        <CircularGaugeComponent id='circulargauge' allowImageExport={true} ref={g => this.circulargauge = g}>
            <Inject services={[ImageExport]} />
        </CircularGaugeComponent>
        </div>)
        }
};
ReactDOM.render(<App />, document.getElementById('circulargauge'));

```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module into `services` and set the [`allowPdfExport`](../api/circular-gauge/#allowpdfexport) property to **true**. The rendered circular gauge can be exported as PDF using the [`export`](../api/circular-gauge/#export) method. The [`export`](../api/circular-gauge/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template="circulargauge/gauge-print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { CircularGaugeComponent, AxesDirective, AxisDirective, PdfExport, Inject, RangesDirective, RangeDirective } from '@syncfusion/ej2-react-circulargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.circular.export('PDF','Gauge', 0);
}
private circular: CircularGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
        <CircularGaugeComponent id='circulargauge' allowPdfExport={true} ref={g => this.circulargauge = g}>
            <Inject services={[PdfExport]} />
        </CircularGaugeComponent>
        </div>)
        }
};
ReactDOM.render(<App />, document.getElementById('circulargauge'));

```

{% endtab %}

>Note: The exporting of the circular gauge as base64 string is not supported in the PDF export.