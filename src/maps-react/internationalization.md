# Internationalization

Maps provides support for internationalization for the below elements.

* Datalabel
* Tooltip

For more information about number and date formatter you can refer
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing an component that works in different
cultures/locales. Internationalization library is used to globalize number, date, time values in
Maps component using [`format`] property in the maps model.

**Numeric Format**

In the below example tooltip is globalized to Deutsch culture.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
import { usa_map } from 'usa.ts';
import { election_data } from 'data.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, MapsTooltip, Inject } from '@syncfusion/ej2-react-maps';
import {Legend, DataLabel} from '@syncfusion/ej2-react-maps';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');

ReactDOM.render(
            <MapsComponent id="maps" format='c' legendSettings={ { visible: true } }
                titleSettings={ { text: 'USA Election Results - 2016' } }>
                <Inject services={[Legend, DataLabel, MapsTooltip]} />
                <LayersDirective>
                    <LayerDirective shapeData={usa_map} shapeDataPath='State' shapePropertyPath='name' dataSource={election_data}
                        shapeSettings={ {
                            colorValuePath: 'Candidate',
                            colorMapping: [
                                { value: 'Trump', color: '#D84444' },
                                { value: 'Clinton', color: '#316DB5' }
                            ]
                        } }
                        dataLabelSettings={ {
                            visible: true,
                            labelPath: 'State',
                            smartLabelMode: 'Trim'
                        } }
                        tooltipSettings={ {
                            visible: true,
                            valuePath: 'value'
                        } }>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);
```

{% endtab %}