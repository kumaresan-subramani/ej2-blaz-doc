---
title: "Editing"
component: "Grid"
description: "Learn how to perform CRUD operations in various edit modes, use different cell editors, and persist data on the server side in the Essential JS 2 DataGrid control."
---

# Editing

The Grid component has options to dynamically insert, delete and update records.
Editing feature requires a primary key column for CRUD operations.
To define the primary key, set [`isPrimaryKey`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~IsPrimaryKey.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper as **true** in particular column.

You can start the edit action either by double clicking the particular row or by selecting the required row and click on **Edit** button in the toolbar. Similarly, you can add a new record to grid either by clicking on **Add** button in the toolbar or an external button which is bound to invoke the **addRecord** method of the grid, **Save** and **Cancel** while in edit mode is possible using respective toolbar icon in grid.

Deletion of the record is possible by selecting the required row and click on **Delete** button in the toolbar.

{% aspTab template="grid/edit/edit", sourceFiles="edit.cs" %}

{% endaspTab %}

> * If [`isIdentity`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~IsIdentity.html) property of **e-grid-column** is enabled, then it will be considered as a read-only column when editing and adding a record.
> * You can disable editing for a particular column, by specifying
[`allowEditing`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~AllowEditing.html) property of **e-grid-column** to **false**.

## Toolbar with edit option

The grid toolbar has the [Built-in items](./tool-bar/#built-in-toolbar-items) to execute Editing actions.
You can define this by using the [`toolbar`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Toolbar.html) property.

{% aspTab template="grid/edit/edittoolbar", sourceFiles="edittoolbar.cs" %}

{% endaspTab %}

## Cell edit type and its params

The [`editType`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~EditType.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper is used to define the editor component for any particular column.

You can set the [`editType`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~EditType.html) based on data type of the column.

* **NumericTextBox** component for integers, double, and decimal data types.

* **TextBox** component for string data type.

* **DropDownList** component to show all unique values related to that field.

* **CheckBox** component for boolean data type.

* **DatePicker** component for date data type.

* **DateTimePicker** component for date time data type.

Also, you can customize the behavior of the editor component through [`edit`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Edit.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper .

The following table describes cell edit type and their corresponding edit params of the column.

Component |Example
-----|-----
`NumericTextBox` | params: { decimals: 2, value: 5 }
`DropDownList` | params: { value: 'Germany' }
`Checkbox` | params: { checked: true}
`DatePicker` | params: { format:'dd.MM.yyyy' }
`DateTimePicker` | params: { value: new Date() }

{% aspTab template="grid/edit/celleditparams", sourceFiles="celleditparams.cs" %}

{% endaspTab %}

> If edit type is not defined in the column, then it will be considered as the **stringedit** type (Textbox component).

## Cell Edit Template

The cell edit template is used to add a custom component for a particular column by invoking the following functions:

* **create** - It is used to create the element at the time of initialization.

* **write** - It is used to create the custom component or assign default value at the time of editing.

* **read** - It is used to read the value from the component at the time of save.

* **destroy** - It is used to destroy the component.

{% aspTab template="grid/edit/celledittemplate", sourceFiles="celledittemplate.cs" %}

{% endaspTab %}

## Edit Modes

Grid supports the following types of edit modes, they are:

* Normal
* Dialog
* Batch

### Normal

In Normal edit mode, when you start editing the currently selected record is changed to edit state.
You can change the cell values and save edited data to the data source.
To enable Normal edit, set [`mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~Mode.html) property of [`e-grid-editSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EditSettings.html) tag helper as **Normal**.

{% aspTab template="grid/edit/inline", sourceFiles="inline.cs" %}

{% endaspTab %}

> Normal edit mode is default mode of editing.

### Dialog

In dialog edit mode, when you start editing the currently selected row data will be shown on a dialog.
You can change the cell values and save edited data to the data source.
To enable Dialog edit, set the [`mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~Mode.html) property of [`e-grid-editSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EditSettings.html) tag helper as **Dialog**.

{% aspTab template="grid/edit/dialog", sourceFiles="dialog.cs" %}

{% endaspTab %}

### Batch

In batch edit mode, when you double-click on the grid cell, then the target cell changed to edit state.
You can bulk save (added, changed and deleted data in the single request) to data source by click on the toolbar's **Update** button or by externally calling the **batchSave** method.
To enable Batch edit, set the [`mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~Mode.html) property of [`e-grid-editSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EditSettings.html) tag helper as **Batch**.

{% aspTab template="grid/edit/batch", sourceFiles="batch.cs" %}

{% endaspTab %}

## Dialog/Inline template

The dialog template editing provides an option to customize the default behavior of dialog editing. Using the dialog template, you can render your own editors by defining the [`mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~Mode.html) property of [`e-grid-editSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~EditSettings.html) tag helper as **Dialog/Inline** and [`template`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~Template.html) property as SCRIPT element ID or HTML string which holds the template.

In some cases, you need to add the new field editors in the dialog which are not present in the column model. In that situation, the template will help you to customize the default edit dialog.

In the below code example, demonstrate the usage of binding a partial view in the dialog template.

{% aspTab template="grid/edit/dialogtemplate", sourceFiles="*.cs" %}

{% endaspTab %}

> The Dialog/Inline template form editors should have **name** attribute.

### Reading Values From Editors

You can read, format and update the current editor value in the [`actionBegin`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionBegin.html) event at the time of **requestType** as **save**.

In the below code example, we have format and updated the **Freight** value.

``` typescript
    function actionBegin(args) {
        if (args.requestType === 'save') {
            // cast string to integer value.
            args.data['Freight'] = parseFloat(args.form.querySelector("#Freight").value);
        }
    }

```

### Set focus to editor

By default, the first input element in the dialog will be focused while opening the dialog.
If the first input element is in disabled or hidden state, focus the valid input element in the
[`actionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionComplete.html)
event based on **requestType** as **beginEdit**.

```typescript

    function actionComplete(args) {
        // Set initail Focus
        if (args.requestType === 'beginEdit') {
            (args.form.elements.namedItem('CustomerID')).focus();
        }
    }

```

### Adding validation rules for custom editors

If you have used additional fields that are not present in the column model, then add the validation rules to the [`actionComplete`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~ActionComplete.html) event.

```typescript

    function actionComplete(args) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            // Add Validation Rules
            args.form.ej2_instances[0].addRules('Freight', {max: 500});
        }
    }

```

## Adding a new row at the Bottom of the Grid

By default, a new row will be added at the top of the grid. You can change it by setting [`newRowPosition`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~NewRowPosition.html) property of [`e-grid-editSettings`] tag helper as **Bottom**.

{% aspTab template="grid/edit/rowposition", sourceFiles="rowposition.cs" %}

{% endaspTab %}

> Add newRowPostion is supported for **Normal** and **Batch** editing modes.

## Default column values on add new record

The grid provides an option to set the default value for the columns when adding a new record in it.
To set a default value for the particular column by defining the [`defaultValue`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~DefaultValue.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper.

{% aspTab template="grid/edit/defaultcolumnvalue", sourceFiles="defaultcolumnvalue.cs" %}

{% endaspTab %}

## Command column

The command column provides an option to add CRUD action buttons in a column. This can be defined by the [`commands`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Commands.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper.

The available built-in command buttons are:

| Command Button | Actions |
|----------------|---------|
| Edit | Edit the current row.|
| Delete | Delete the current row.|
| Save | Update the edited row.|
| Cancel | Cancel the edited state. |

{% aspTab template="grid/edit/commandcolumn", sourceFiles="commandcolumn.cs" %}

{% endaspTab %}

### Custom command

The custom command buttons can be added in a column by using the [`commands`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~Commands.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.Grid~Columns.html) tag helper and
the action for the custom buttons can be defined using **commandClick** event.

{% aspTab template="grid/edit/customcommand", sourceFiles="customcommand.cs" %}

{% endaspTab %}

## Confirmation messages

### Delete confirmation

The delete confirm dialog can be shown when deleting a record by defining the [`showDeleteConfirmDialog`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~ShowDeleteConfirmDialog.html) property of [`e-grid-editSettings`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings.html) as **true**.

{% aspTab template="grid/edit/deleteconfirm", sourceFiles="deleteconfirm.cs" %}

{% endaspTab %}

> The [`showDeleteConfirmDialog`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~ShowDeleteConfirmDialog.html) supports all type of edit modes.

### Batch confirmation

By default, grid will show the confirm dialog when saving or cancelling or performing any actions like filtering, sorting, etc.

{% aspTab template="grid/edit/batchconfirm", sourceFiles="batchconfirm.cs" %}

{% endaspTab %}

> * [`showConfirmDialog`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~ShowConfirmDialog.html) requires the [`mode`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~Mode.html) to be **Batch**.
> * If [`showConfirmDialog`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridEditSettings~ShowConfirmDialog.html) set to **false**, then confirmation dialog does not display in batch editing.

## Column validation

Column validation allows you to validate the edited or added row data and it display errors for invalid fields before saving data.
Grid uses **Form Validator** component for column validation.
You can set validation rules in [`validationRules`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~ValidationRules.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) tag helper.

{% aspTab template="grid/edit/columnvalid", sourceFiles="columnvalid.cs" %}

{% endaspTab %}

### Custom validation

You can define your own custom validation rules for the specific columns by using **Form Validator custom rules**.

In the below demo, custom validation applied for **CustomerID** column.

{% aspTab template="grid/edit/customvalidation", sourceFiles="customvalidation.cs" %}

{% endaspTab %}

## Persisting data in server

Edited data can be persisted in the database using the RESTful web services.

All the CRUD operations in the grid are done through **DataManager**. The **DataManager** has an option to bind all the CRUD related data in server-side.

> For your information, the ODataAdaptor persists data in the server as per OData protocol.

In the below section, we have explained how to get the edited data details on the server-side using the **UrlAdaptor**.

### URL adaptor

You can use the **UrlAdaptor** of **DataManager** when binding data source from remote data.
In the initial load of grid, data are fetched from remote data and bound to the grid using **url** property of **DataManager**.
You can map The CRUD operation in grid can be mapped to server-side Controller actions using the properties **InsertUrl**, **RemoveUrl**, **UpdateUrl**, **CrudUrl** and **BatchUrl**.

The following code example describes the above behavior.

{% aspTab template="grid/edit/urladaptor", sourceFiles="urladaptor.cs" %}

{% endaspTab %}

Also, when using the **UrlAdaptor**, you need to return the data as JSON from the controller action and the JSON object must contain a property as **result** with dataSource as its value and one more property **count** with the dataSource total records count as its value.

The following code example describes the above behavior.

{% aspTab template="grid/edit/urladaptor", sourceFiles="data.cs" %}

{% endaspTab %}

### Insert record

Using the **InsertUrl** property, you can specify the controller action mapping URL to perform insert operation on the server-side.

The following code example describes the above behavior.

{% aspTab template="grid/edit/urladaptor", sourceFiles="insert.cs" %}

{% endaspTab %}

> If you get posted data as **null** at the server side, then it might be due to the model state failure. You can check this using **ModelState.IsValid** and get the failure error details using **ModelState.Values** property.

The newly added record details are bound to the **value** parameter. Please refer to the following screenshot.

![insert](./images/insert.jpg)

### Update record

Using the **UpdateUrl** property, the controller action mapping URL can be specified to perform save/update operation on the server-side.

The following code example describes the previous behavior.

{% aspTab template="grid/edit/urladaptor", sourceFiles="update.cs" %}

{% endaspTab %}

> If you get posted data as **null** at the server side, then it might be due to the model state failure. You can check this using **ModelState.IsValid** and get the failure error details using **ModelState.Values** property.

The updated record details are bound to the **value** parameter. Please refer to the following screenshot.

![update](./images/update.jpg)

### Delete record

Using the **RemoveUrl** property, the controller action mapping URL can be specified to perform delete operation on the server-side.

The following code example describes the previous behavior.

{% aspTab template="grid/edit/urladaptor", sourceFiles="delete.cs" %}

{% endaspTab %}

> If you get posted data as **null** at the server side, then it might be due to the model state failure. You can check this using **ModelState.IsValid** and get the failure error details using **ModelState.Values** property.

The deleted record primary key value is bound to the **key** parameter. Please refer to the following screenshot.

![delete](./images/delete.jpg)

### CRUD URL

Using the **CrudUrl** property, the controller action mapping URL can be specified to perform all the CRUD operation at server-side using a single method instead of specifying separate controller action method for CRUD (insert, update and delete) operations.

The action parameter of **CrudUrl** is used to get the corresponding CRUD action.

The following code example describes the above behavior.

{% aspTab template="grid/edit/crudurl", sourceFiles="crudurl.cs" %}

{% endaspTab %}

Please refer to the following screenshot to know about the action parameter.

![crudupdate](./images/crudupdate.jpg)

> If you specify **InsertUrl** along with **CrudUrl**, then while adding **InsertUrl** only will be invoked.
> If you get posted data as **null** at the server side, then it might be due to the model state failure. You can check this using **ModelState.IsValid** and get the failure error details using **ModelState.Values** property.

### Batch URL

The **BatchUrl** property supports only for batch editing mode.
You can specify the controller action mapping URL to perform batch operation on the server-side.

The following code example describes the above behavior.

{% aspTab template="grid/edit/batchurl", sourceFiles="batchurl.cs" %}

{% endaspTab %}

> If you get posted data as **null** at the server side, then it might be due to the model state failure. You can check this using **ModelState.IsValid** and get the failure error details using **ModelState.Values** property.

```typescript
public ActionResult BatchUpdate([FromBody]string action, List<EditableOrder> added, List<EditableOrder> changed, List<EditableOrder> deleted, int? key)
{
//Save the batch changes in database
}
```

![batch](./images/batch.jpg)

## Disable editing for particular column

You can disable editing for particular columns by using the [`allowEditing`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/aspnetcore/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn~AllowEditing.html) property of [`e-grid-column`](https://help.syncfusion.com/cr/cref_files/aspnetcore-js2/Syncfusion.EJ2~Syncfusion.EJ2.Grids.GridColumn.html) tag helper.

In the following demo, editing is disabled for the **CustomerID** column.

{% aspTab template="grid/edit/disableeditforcolumn", sourceFiles="disableeditforcolumn.cs" %}

{% endaspTab %}

## Troubleshoot: Editing works only for first row

The Editing functionalities can be performed based upon the primary key value of the selected row.
If **primaryKey** is not defined in the grid, then edit or delete action take places the first row.

## See also

* [Editing with template column](./how-to/editing-with-template-column)
* [Customize dialog when editing](./how-to/customize-the-edit-dialog)
* [Cascading DropDownList with Grid Editing](./how-to/provide-custom-data-source-and-enabling-filtering-to-drop-down-list)
* [Access Editor components](./how-to/access-editor-components)
* [Customize the Edit Dialog](./how-to/customize-the-edit-dialog)
* [Wizard Like Editing](./how-to/use-wizard-like-dialog-editing)
* [Tab Inside the Dialog Template](./how-to/using-tab-inside-the-dialog-editing)
* [Restrict to type decimal points in a NumericTextBox while editing the numeric column](./how-to/restrict-decimal-points-while-grid-editing)
