---
title: "Autocomplete Localization"
component: "AutoComplete"
description: "This section explains the localization support of the Syncfusion JavaScript autocomplete control."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/auto-complete/#norecordstemplate)
 and [actionFailureTemplate](../api/auto-complete/#actionfailuretemplate)
&nbsp;properties according to the culture currently assigned to the AutoComplete.

| Locale key | en-US (default)  |
|------|------|
| noRecordsTemplate |  No Records Found |
| actionFailureTemplate | The Request Failed |

## Loading translations

To load translation object to your application, use load function of the **L10n** class.

In the following sample, French culture is set to the AutoComplete and no data is loaded. Hence, the
`noRecordsTemplate` property displays its text in French culture initially and if the sample
is run offline, the `actionFailureTemplate` property displays its text appropriately.

{% tab template="autocomplete/basic", es5Template="basic-locale" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
// import L10n class for load function
import { L10n, setCulture } from '@syncfusion/ej2-base';
import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';

let atcObj: AutoComplete = new AutoComplete({
    // bind remote data to showcase actionFailureTemplate in offline.
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().select(['ContactName', 'CustomerID']).take(0),
    //map the appropriate columns to fields property
    fields: { value: 'ContactName' },
    // set locale culture to AutoComplete
    locale: 'fr-BE',
    // set placeholder to AutoComplete input element
    placeholder: 'Trouver un client'
});
atcObj.appendTo('#atcelement');

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
* [How to bind the data to the autocomplete](./data-binding)