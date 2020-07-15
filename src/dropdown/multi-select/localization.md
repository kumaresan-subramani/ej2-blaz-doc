---
title: "Multiselect Localization"
component: "MultiSelect"
description: "This section explains the localization support of Syncfusion JavaScript multiselect control."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/multi-select/#norecordstemplate)
 and [actionFailureTemplate](../api/multi-select/#actionfailuretemplate)
&nbsp;properties according to the culture currently assigned to the MultiSelect.

| Locale key | en-US (default)  |
|------|------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use load function of the **L10n** class.

In the following sample, French culture is set to the MultiSelect and no data is loaded. Hence, the [`noRecordsTemplate`](../api/multi-select/#norecordstemplate) property displays its text in French culture initially, and if the sample is run offline, the [`actionFailureTemplate`](../api/multi-select/#actionfailuretemplate) property displays its text appropriately.

{% tab template="multiselect/basic", es5Template="basic-local" %}

```typescript

import { MultiSelect } from '@syncfusion/ej2-dropdowns';
// import L10n class for load function
import { L10n, setCulture} from '@syncfusion/ej2-base';
import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';

// bind remotedata to showcase actionFailureTemplate in offline.
let customerData: DataManager = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

let msObj: MultiSelect = new MultiSelect({
    dataSource: customerData,
    // set locale culture to MultiSelect
    locale: 'fr-BE',
    // map appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // take 0 item to showcase noRecordsTemplate property.
    query: new Query().select(['ContactName', 'CustomerID']).take(0),
    // set placeholder to MultiSelect input element
    placeholder: 'Sélectionnez un éléments'
});
msObj.appendTo('#select');

L10n.load({
    'fr-BE': {
       'dropdowns': {
             'noRecordsTemplate': "Aucun enregistrement trouvé",
             'actionFailureTemplate': "Modèle d'échec d'action"
         }
     }
});

```

{% endtab %}

## See Also

* [Accessibility](./accessibility)
* [How to bind the data to the combobox](./data-binding)