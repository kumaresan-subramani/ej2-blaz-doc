# Data labels

Data labels provide information to users about the shapes of the Maps component.

## Add data labels

You can add label text to the shapes of the Maps component using `dataLabelSettings`. The following sample demonstrates the names of all the states n the United States in data labels.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, DataLabel } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[DataLabel]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map}
                                    shapeSettings= {{
                                        autofill: true
                                    }}
                     dataLabelSettings={ {
                            visible: true,
                            labelPath: 'name',
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

> The `autofill` property is used in `shapeSettings` to apply the default palette colors to the shapes.

Some data labels intersect with other labels in this output. The following options are used to avoid intersecting:

## Smart labels

The Maps component provides an option to specify the smart labels when the labels intersect with the corresponding shape borders. In the `smartLabelMode` property, you can specify any of the following options:

* None
* Hide
* Trim

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, DataLabel } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[DataLabel]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map}
                                    shapeSettings= {{
                                        autofill: true
                                    }}
                     dataLabelSettings={ {
                            visible: true,
                            labelPath: 'name',
                            smartLabelMode: 'Hide'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Intersect action

This specifies the intersect action when a label intersect with another label. In the `intersectionAction` property, you can specify any of the following options:

* None
* Hide
* Trim

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx

import { world_map } from 'world-map.ts';
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Inject, DataLabel } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
            <Inject services={[DataLabel]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map}
                                    shapeSettings= {{
                                        autofill: true
                                    }}
                     dataLabelSettings={ {
                            visible: true,
                            labelPath: 'name',
                            intersectionAction: 'Trim'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}