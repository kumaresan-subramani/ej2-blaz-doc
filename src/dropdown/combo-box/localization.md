---
title: "Combo box Localization"
component: "ComboBox"
description: "This section explains the localization support of Syncfusion JavaScript combo box control."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/combo-box/#norecordstemplate)
 and [actionFailureTemplate](../api/combo-box/#actionfailuretemplate)
&nbsp;properties according to the culture currently assigned to the ComboBox.

| Locale key | en-US (default)  |
|------|------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use `load` function of **L10n** class.

In the following sample, French culture is set to the ComboBox and no data is loaded. Hence, the [`noRecordsTemplate`](../api/combo-box/#norecordstemplate) property displays its text in French culture initially, and if the sample is run offline, the [`actionFailureTemplate`](../api/combo-box/#actionfailuretemplate) property displays its text appropriately.

{% tab template="combobox/basic",es5Template="basic-locale" %}

```typescript

import { ComboBox } from '@syncfusion/ej2-dropdowns';
// import L10n class for load function
import { L10n, setCulture} from '@syncfusion/ej2-base';
import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';
// bind remotedata to showcase actionFailureTemplate in offline.
let customerData: DataManager = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

let ComboBoxObj: ComboBox = new ComboBox({
    dataSource: customerData,
    // set locale culture to ComboBox
    locale: 'fr-BE',
    // map appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // take 0 item to showcase noRecordsTemplate property.
    query: new Query().select(['ContactName', 'CustomerID']).take(0);
    // set placeholder to ComboBox input element
    placeholder: 'Sélectionnez un client'
});
ComboBoxObj.appendTo('#comboelement');

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