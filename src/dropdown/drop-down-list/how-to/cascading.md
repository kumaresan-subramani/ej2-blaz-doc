---
title: "Drop-down list cascading"
component: "DropDownList"
description: "This section explains on how to acheive cascading fuctionality in Syncfusion JavaScript drop-down list control."
---

# Configure the Cascading DropDownList

The cascading DropDownList is a series of DropDownList, where the value of one DropDownList depends
upon  another's value. This can be configured by using the [`change`](../../api/drop-down-list/#change) event of the parent DropDownList.
Within that change event handler, data has to be loaded to the child DropDownList based on the selected
value of the parent DropDownList.

The following example, shows the cascade behavior of country, state, and city
DropDownList. Here, the [`dataBind`](../../api/drop-down-list/#databind) method is used to reflect the property changes immediately
to the DropDownList.

{% tab template="dropdownlist/cascading", es5Template="cascading", sourceFiles="app.ts,index.html" %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Query } from '@syncfusion/ej2-data';

//define the country DropDownList data
let countryData: { [key: string]: Object }[] = [
    { CountryName: 'United States', CountryId: '1' },
    { CountryName: 'Australia', CountryId: '2' }
];
//define the state DropDownList data
let stateData: { [key: string]: Object }[] = [
    { StateName: 'New York', CountryId: '1', StateId: '101' },
    { StateName: 'Virginia ', CountryId: '1', StateId: '102' },
    { StateName: 'Tasmania ', CountryId: '2', StateId: '105' }
];
//define the city DropDownList data
let cityData: { [key: string]: Object }[] = [
    { CityName: 'Albany', StateId: '101', CityId: 201 },
    { CityName: 'Beacon ', StateId: '101', CityId: 202 },
    { CityName: 'Hampton ', StateId: '102', CityId: 205 },
    { CityName: 'Emporia', StateId: '102', CityId: 206 },
    { CityName: 'Hobart', StateId: '105', CityId: 213 },
    { CityName: 'Launceston ', StateId: '105', CityId: 214 }
];
//initiates the country DropDownList
let countryObj: DropDownList = new DropDownList({
    dataSource: countryData,
    fields: { value: 'CountryId', text: 'CountryName' },
    //bind the change event handler
    change: () => {
        //Query the data source based on country DropDownList selected value
        stateObj.query = new Query().where('CountryId', 'equal', countryObj.value);
        // enable the state DropDownList
        stateObj.enabled = true;
        //clear the existing selection.
        stateObj.text = null;
        // bind the property changes to state DropDownList
        stateObj.dataBind();
        //clear the existing selection in city DropDownList
        cityObj.text = null;
        //disabe the city DropDownList
        cityObj.enabled = false;
        //bind the property cahnges to City DropDownList
        cityObj.dataBind();
    },
    placeholder: 'Select a country',
});
//render the country DropDownList
countryObj.appendTo('#countries');

//initiates the state DropDownList
let stateObj: DropDownList = new DropDownList({
    dataSource: stateData,
    fields: { value: 'StateId', text: 'StateName' },
    // set disable state by default to prevent user interact.
    enabled: false,
    change: () => {
        // Query the data source based on state DropDownList selected value
        cityObj.query = new Query().where('StateId', 'equal', stateObj.value);
        // enable the city DropDownList
        cityObj.enabled = true;
        //clear the existing selection
        cityObj.text = null;
        // bind the property change to city DropDownList
        cityObj.dataBind();
    },
    placeholder: 'Select a state',
});
//render the state DropDownList
stateObj.appendTo('#states');

//initiates the city DropDownList
let cityObj: DropDownList = new DropDownList({
    dataSource: cityData,
    fields: { text: 'CityName', value: 'CityId' },
    // disable the DropDownList by default to prevent the user interact.
    enabled: false,
    placeholder: 'Select a city',
});
//render the city DropDownList
cityObj.appendTo('#cities');

```

{% endtab %}