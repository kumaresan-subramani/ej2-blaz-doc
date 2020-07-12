# Print and Export

## Print

To use the print functionality, we should inject the `Print` module into `services` and set the [`allowPrint`](../api/linear-gauge/#allowprint) property to **true**. The rendered linear gauge can be printed directly from the browser by calling the method [`print`](../api/linear-gauge/#print).

{% tab template="linear-gauge/print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { LinearGaugeComponent, AxesDirective, Print, Inject, AxisDirective, PointersDirective, PointerDirective } from '@syncfusion/ej2-react-lineargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.linear.print();
}
private linear: LinearGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='print' onClick= { this.clickHandler.bind(this)}>print</ButtonComponent>
        <LinearGaugeComponent id='gauge' allowPrint={true}  ref={g => this.gauge = g}>
            <Inject services={[Print]} />
        </LinearGaugeComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('gauge'));

```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module into `services` and set the [`allowImageExport`](../api/linear-gauge/#allowimageexport) property to **true**. The rendered linear gauge can be exported as an image using the [`export`](../api/linear-gauge/#export) method. The method requires two parameters: image type and file name. The gauge can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template="linear-gauge/print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { LinearGaugeComponent, AxesDirective, ImageExport, Inject, AxisDirective, PointersDirective, PointerDirective } from '@syncfusion/ej2-react-lineargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.linear.export('PNG','Gauge');
}
private linear: LinearGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
        <LinearGaugeComponent id='gauge' allowImageExport={true} ref={g => this.gauge = g}>
            <Inject services={[ImageExport]} />
        </LinearGaugeComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('gauge'));

```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The linear gauge can be exported to image as a base64 string using the [`export`](../api/linear-gauge/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template="linear-gauge/print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { LinearGaugeComponent, AxesDirective, ImageExport, Inject, AxisDirective, PointersDirective, PointerDirective } from '@syncfusion/ej2-react-lineargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
    this.linear.export('PNG', 'Gauge', null, false).then((data: string)=>{
        document.writeln(data);
    })
}
private linear: LinearGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>Export</ButtonComponent>
        <LinearGaugeComponent id='gauge' allowImageExport={true} ref={g => this.gauge = g}>
            <Inject services={[ImageExport]} />
        </LinearGaugeComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('gauge'));

```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module into `services` and set the [`allowPdfExport`](../api/linear-gauge/#allowpdfexport) property to **true**. The rendered linear gauge can be exported as PDF using the [`export`](../api/linear-gauge/#export) method. The [`export`](../api/linear-gauge/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template="linear-gauge/print-and-export", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { LinearGaugeComponent, AxesDirective, PdfExport, Inject, AxisDirective, PointersDirective, PointerDirective } from '@syncfusion/ej2-react-lineargauge';
class App extends React.Component<{}, {}>{
public clickHandler(){
  this.linear.export('PDF', 'Gauge', 0);
}
private linear: LinearGaugeComponent;
render(){
        return (<div>
        <ButtonComponent value='export' onClick= { this.clickHandler.bind(this)}>print</ButtonComponent>
        <LinearGaugeComponent id='gauge' allowPdfExport={true} ref={g => this.gauge = g}>
            <Inject services={[PdfExport]} />
        </LinearGaugeComponent></div>)
        }
};
ReactDOM.render(<App />, document.getElementById('gauge'));

```

{% endtab %}

>Note: The exporting of the linear gauge as base64 string is not supported in the PDF export.