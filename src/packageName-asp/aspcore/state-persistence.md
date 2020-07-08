---
title: "State Persistence"
component: "Grid"
description: "Learn how to persist the DataGrid state and model in the browser’s local storage."
---

# State Persistence

State persistence refers to the Grid's state maintained in the browser's [`localStorage`](https://www.w3schools.com/html/html5_webstorage.asp#) even if the browser is refreshed or if you move to the next page within the browser.
State persistence stores grid’s model object in the local storage when the [`enablePersistence`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EnablePersistence.html) is defined as true.

## Maintaining custom query in a persistent state

The grid does not maintain the query params after page load event when the [`enablePersistence`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EnablePersistence.html) is set to true. This is because the grid refreshes its query params for every page load. You can maintain the custom query params by resetting the **addParams** method in [`actionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionBegin.html) event.

{% aspTab template="grid/state-persist/state-persist", sourceFiles="state-persist.cs" %}

{% endaspTab %}

## Get or set localStorage value

If the [`enablePersistence`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EnablePersistence.html) property is set to true, the grid property value is saved in the **window.localStorage** for reference. You can get/set the localStorage value by using the **getItem**/**setItem** method in the **window.localStorage**.

```typescript
//get the Grid model.
var value = window.localStorage.getItem('gridGrid'); //"gridGrid" is component name + component id.
var model= JSON.parse(model);

```

```typescript
//set the Grid model.
window.localStorage.setItem('gridGrid', JSON.stringify(model)); //"gridGrid" is component name + component id.

```