---
title: "Autocomplete Filtering"
component: "AutoComplete"
description: "This section for Syncfusion JavaScript autocomplete control explains the built-in filtering support with a rich set of filtering configurations."
---

# Filtering

The AutoComplete has built-in support to filter data items. The filter operation
starts as soon as you start typing characters in the component.

## Change the filter type

Determines on which filter type, the component needs to be considered on search action.
The available [`filterType`](../api/auto-complete/#filtertype) and its supported data types are

| **Filter Type** | **Description** | **Supported Types** |
| --- | --- |
| StartsWith | Checks whether a value begins with the specified value. | String |
| EndsWith | Checks whether a value ends with specified value. | String |
| Contains | Checks whether a value contains with specified value. | String |

The following examples shows the data filtering is done with `StartsWith` type.

{% tab template="autocomplete/basic", es5Template="basic-filter" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
//initiates the component
let filter: AutoComplete = new AutoComplete({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().select(['ContactName']),
    //map the appropriate columns to fields property
    fields: { value: 'ContactName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a customer",
    //set the filterType to searching operation
    filterType: 'StartsWith',
    //sort the resulted items
    sortOrder: 'Ascending'
});
filter.appendTo('#atcelement');

```

{% endtab %}

## Filter item count

You can specify the filter suggestion item count through
[`suggestionCount`](../api/auto-complete/#suggestioncount) property of AutoComplete.

The following example, to restrict the suggestion list item counts as 5.

{% tab template="autocomplete/basic", es5Template="item-count"%}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
//initiates the component
let filter: AutoComplete = new AutoComplete({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().select(['ContactName', 'CustomerID']),
    //set the suggestionCount to show the maximum suggestion list item
    suggestionCount: 5,
    //map the appropriate columns to fields property
    fields: { value: 'ContactName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a customer",
    //sort the resulted items
    sortOrder: 'Ascending'
});
filter.appendTo('#atcelement');

```

{% endtab %}

## Limit the minimum filter character

You can set the limit for the character count to filter the data on the AutoComplete. This can be done by
set the [`minLength`](../api/auto-complete/#minlength) property to AutoComplete.

In the following example, the remote request doesn't fetch the search data, until the search key contains three characters.

{% tab template="autocomplete/basic", es5Template="limit-filter"%}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';
//initiates the component
let filter: AutoComplete = new AutoComplete({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().select(['ContactName', 'CustomerID']),
    //set the minLength to restrict the remote request until search key contains 3 characters.
    minLength: 3,
    //map the appropriate columns to fields property
    fields: { value: 'ContactName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a customer",
    //set the filterType to searching operation
    filterType: 'StartsWith',
    //sort the resulted items
    sortOrder: 'Ascending'
});
filter.appendTo('#atcelement');

```

{% endtab %}

## Case sensitive filtering

Data items can be filtered either with or without case sensitivity using the DataManager.
This can be done by setting the [`ignoreCase`](../api/auto-complete/#ignorecase) property of AutoComplete.

The following sample depicts how to filter the data with case-sensitive.

{% tab template="autocomplete/basic", es5Template="case-sensitive-filter" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
//import DataManager related classes
import { Query, DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';
//initiates the component
let filter: AutoComplete = new AutoComplete({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
        url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/',
        crossDomain: true
    }),
    //bind the Query instance to query property
    query: new Query().from('Customers').select('ContactName').take(7),
    //map the appropriate columns to fields property
    fields: { value: 'ContactName' },
    //set the placeholder to AutoComplete input
    placeholder: "Find a customer",
    //set the ignoreCase as false to enable the case sensitive filtering
    ignoreCase: false,
    //set the filterType to searching operation
    filterType: 'StartsWith',
    //sort the resulted items
    sortOrder: 'Ascending'
});

filter.appendTo('#atcelement');

```

{% endtab %}

## Diacritics Filtering

An AutoComplete supports diacritics filtering which will ignore the [diacritics](https://en.wikipedia.org/wiki/Diacritic) and makes it easier to filter the results in international characters lists when the [ignoreAccent](../api/auto-complete/#ignoreaccent) is enabled.

In the following sample,data with diacritics are bound as dataSource for AutoComplete.

{% tab template="autocomplete/basic", es5Template="diacritics-filtering" %}

```typescript

import { AutoComplete } from '@syncfusion/ej2-dropdowns';
   // create local data
    let data: string[] = [
        'Aeróbics',
        'Aeróbics en Agua',
        'Aerografía',
        'Aeromodelaje',
        'Águilas',
        'Ajedrez',
        'Ala Delta',
        'Álbumes de Música',
        'Alusivos',
        'Análisis de Escritura a Mano'];
    // initialize AutoComplete component
    let atcObj: AutoComplete = new AutoComplete({
        //set the local data to dataSource property
        dataSource: data,
        // set the placeholder to AutoComplete input element
        placeholder: 'e.g: aero',
        // enabled the ignoreAccent property for ignore the diacritics
        ignoreAccent: true
    });
    atcObj.appendTo('#atcelement');

```

{% endtab %}

## See Also

* [How to acheive autofill while filtering](./how-to/autofill/)
* [How to group the data using header](./grouping)
* [How to highlight the search data](./how-to/custom-search/)