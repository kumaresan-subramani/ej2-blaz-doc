
# Print and Export

## Print

To use the print functionality, we should inject the `Print` module and set the [`allowPrint`](../api/circular-gauge/#allowprint) property to **true**. The rendered circular gauge can be printed directly from the browser by calling the method [`print`](../api/circular-gauge/#print).

<!-- markdownlint-disable MD036 -->

{% tab template= "circular-gauge/gauge-print", sourceFiles="index.ts,index.html", es5Template="es5Print" %}

```typescript
import { CircularGauge, Print } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Print);
let gauge: CircularGauge = new CircularGauge({
    allowPrint: true
}, '#element');
document.getElementById('print').onclick = () => {
        gauge.print();
};
```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module and set the [`allowImageExport`](../api/circular-gauge/#allowimageexport) property to **true**. The rendered circular gauge can be exported as an image using the [`export`](../api/circular-gauge/#export) method. The method requires two parameters: image type and file name. The circular gauge can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template= "circular-gauge/gauge-export", sourceFiles="index.ts,index.html", es5Template="es5Export" %}

```typescript
import { CircularGauge, ImageExport} from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(ImageExport);
let gauge: CircularGauge = new CircularGauge({
    allowImageExport: true
}, '#element');
document.getElementById('export').onclick = () => {
        gauge.export("PNG","Gauge");
};
```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The circular gauge can be exported to image as a base64 string using the [`export`](../api/circular-gauge/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template= "circular-gauge/gauge-export", sourceFiles="index.ts,index.html", es5Template="es5Base64" %}

```typescript
import { CircularGauge, ImageExport } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(ImageExport);
let gauge: CircularGauge = new CircularGauge({
    allowImageExport: true
}, '#element');
document.getElementById('export').onclick = () => {
    gauge.export('JPEG', 'Gauge', null, false).then((data) => {
            let base64 = data;
            document.writeln(base64);
        });
};
```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module and set the [`allowPdfExport`](../api/circular-gauge/#allowpdfexport) property to **true**. The rendered circular gauge can be exported as PDF using the [`export`](../api/circular-gauge/#export) method. The [`export`](../api/circular-gauge/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template= "circular-gauge/gauge-export", sourceFiles="index.ts,index.html", es5Template="es5ExportPdf" %}

```typescript
import { CircularGauge, PdfExport } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(PdfExport);
let gauge: CircularGauge = new CircularGauge({
    allowPdfExport: true
}, '#element');
document.getElementById('export').onclick = () => {
    gauge.export("PDF", "Gauge", 0);
};
```

{% endtab %}

>Note: The exporting of the circular gauge as base64 string is not supported in the PDF export.
