# Print and Export

## Print

To use the print functionality, we should inject the `Print` module and set the [`allowPrint`](../api/maps/#allowprint) property to **true**. The rendered map can be printed directly from the browser by calling the method [`print`](../api/maps/#print).

{% tab template="maps/print", sourceFiles="index.ts,index.html", es5Template="print" %}

```typescript

import { Maps, MapsTooltip, DataLabel, Print} from '@syncfusion/ej2-maps';
import { usa_map } from '../default-map-cs1/usa.ts';
Maps.Inject(MapsTooltip, DataLabel, Print);
    let maps: Maps = new Maps({
        allowPrint: true,
        layers: [
            {
                dataLabelSettings: {
                    visible: true,
                    labelPath: 'name',
                    smartLabelMode: 'Trim'
                },
                shapeData: usa_map,
                shapeSettings: {
                    autofill: true
                },
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                },
            }
        ]
    });
    maps.appendTo('#element');
    document.getElementById('print').onclick = () => {
        maps.print();
    };

```

{% endtab %}

## Export

### Image Export

To use the image export functionality, we should inject the `ImageExport` module and set the [`allowImageExport`](../api/maps/#allowimageexport) property to **true**. The rendered map can be exported as an image using the [`export`](../api/maps/#export) method. The method requires two parameters: image type and file name. The map can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template="maps/export", sourceFiles="index.ts,index.html", es5Template="export" %}

```typescript

import { Maps, MapsTooltip, DataLabel, ImageExport} from '@syncfusion/ej2-maps';
import { usa_map } from '../default-map-cs1/usa.ts';
Maps.Inject(MapsTooltip, DataLabel, ImageExport );

    let maps: Maps = new Maps({
        allowImageExport: true,
        layers: [
            {
                dataLabelSettings: {
                    visible: true,
                    labelPath: 'name',
                    smartLabelMode: 'Trim'
                },
                shapeData: usa_map,
                shapeSettings: {
                    autofill: true
                },
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                },
            }
        ]
    });
    maps.appendTo('#element');
    document.getElementById('export').onclick = () => {
        maps.export('PNG', 'Maps');
    };

```

{% endtab %}

We can get the image file as base64 string for the JPEG and PNG formats. The rendered map can be exported to image as a base64 string using the [`export`](../api/maps/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template="maps/export", sourceFiles="index.ts,index.html", es5Template="base64" %}

```typescript

import { Maps, MapsTooltip, DataLabel, ImageExport} from '@syncfusion/ej2-maps';
import { usa_map } from '../default-map-cs1/usa.ts';
Maps.Inject(MapsTooltip, DataLabel, ImageExport);

    let maps: Maps = new Maps({
        allowImageExport: true,
        layers: [
            {
                dataLabelSettings: {
                    visible: true,
                    labelPath: 'name',
                    smartLabelMode: 'Trim'
                },
                shapeData: usa_map,
                shapeSettings: {
                    autofill: true
                },
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                },
            }
        ]
    });
    maps.appendTo('#element');
    document.getElementById('export').onclick = () => {
        maps.export('JPEG', 'Maps', null, false).then((data) => {
            let base64 = data;
            document.writeln(base64);
        });
    };

```

{% endtab %}

### PDF Export

To use the PDF export functionality, we should inject the `PdfExport` module and set the [`allowPdfExport`](../api/maps/#allowpdfexport) property to **true**. The rendered map can be exported as PDF using the [`export`](../api/maps/#export) method. The [`export`](../api/maps/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template="maps/export", sourceFiles="index.ts,index.html", es5Template="exportPdf" %}

```typescript

import { Maps, MapsTooltip, DataLabel, PdfExport} from '@syncfusion/ej2-maps';
import { usa_map } from '../default-map-cs1/usa.ts';
Maps.Inject(MapsTooltip, DataLabel, PdfExport);

    let maps: Maps = new Maps({
        allowPdfExport: true,
        layers: [
            {
                dataLabelSettings: {
                    visible: true,
                    labelPath: 'name',
                    smartLabelMode: 'Trim'
                },
                shapeData: usa_map,
                shapeSettings: {
                    autofill: true
                },
                tooltipSettings: {
                    visible: true,
                    valuePath: 'name'
                },
            }
        ]
    });
    maps.appendTo('#element');
    document.getElementById('export').onclick = () => {
        maps.export('PDF', 'Maps', 0);
    };

```

{% endtab %}

>Note: The exporting of the map as base64 string is not supported in the PDF export.

<!-- markdownlint-disable MD010 -->

### Export the tile maps

The rendered map with providers such as OSM, Bing and Google static maps can be exported using the [`export`](../api/maps/#export) method. It supports the following export formats.

* JPEG
* PNG
* PDF

{% tab template="maps/OSMPrintExport", sourceFiles="index.ts,index.html", es5Template="OSMPrintExport" %}

```typescript

import { Maps, Print, ImageExport, PdfExport} from '@syncfusion/ej2-maps';
Maps.Inject(Print, ImageExport, PdfExport);
    let maps: Maps = new Maps({
        allowPdfExport: true,
        allowImageExport: true,
        allowPrint: true,
        titleSettings: {
			text: 'OSM'
		},
        layers: [
            {
                layerType: 'OSM'
            }
        ]
    });
    maps.appendTo('#container');
    document.getElementById('export').onclick = () => {
        maps.export('PNG', 'Maps');
    };
    document.getElementById('print').onclick = () => {
        maps.print();
    };

```

{% endtab %}