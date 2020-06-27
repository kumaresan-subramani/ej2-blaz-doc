---
title: "Form fields"
component: "DocumentEditor"
description: "Learn how to use form fields in JavaScript document editor"
---

# Form Fields

DocumentEditorContainer component provide support for inserting Text, CheckBox, DropDown form fields through in-built toolbar.

![Form Fields](images/toolbar-form-fields.png)

## Insert form field

Form fields can be inserted using [`insertFormField`](../api/document-editor/editor/#insertformfield) method in editor module.

```typescript
//Insert Text form field
documentEditor.editor.insertFormField('Text');
//Insert Checkbox form field
documentEditor.editor.insertFormField('CheckBox');
//Insert Drop down form field
documentEditor.editor.insertFormField('Dropdown');
```

## Get form field names

All the form fields names form current document can be retrieved using [`getFormFieldNames()`](../api/document-editor/#getformfieldnames).

```typescript
let formFieldsNames: string[] = documentEditor.getFormFieldNames();
```

## Get form field properties

Form field properties can be retrieved using [`getFormFieldInfo()`](../api/document-editor/#getformfieldinfo).

```typescript
//Text form field
let textfieldInfo: TextFormFieldInfo = documentEditor.getFormFieldInfo('Text1') as TextFormFieldInfo;
//Checkbox form field
let checkboxfieldInfo: CheckBoxFormFieldInfo = documentEditor.getFormFieldInfo('Check1') as CheckBoxFormFieldInfo;
//Dropdown form field
let dropdownfieldInfo: DropDownFormFieldInfo = documentEditor.getFormFieldInfo('Drop1') as DropDownFormFieldInfo;
```

## Set form field properties

Form field properties can be modified using [`setFormFieldInfo`](../api/document-editor/#setformfieldInfo).

```typescript
// Set text form field properties
let textfieldInfo: TextFormFieldInfo = documentEditor.getFormFieldInfo('Text1') as TextFormFieldInfo;
textfieldInfo.defaultValue = "Hello";
textfieldInfo.format = "Uppercase";
textfieldInfo.type = "Text";
documentEditor.setFormFieldInfo('Text1',textfieldInfo);

// Set checkbox form field properties
let checkboxfieldInfo: CheckBoxFormFieldInfo = documentEditor.getFormFieldInfo('Check1') as CheckBoxFormFieldInfo;
checkboxfieldInfo.defaultValue = true;
documentEditor.setFormFieldInfo('Check1',checkboxfieldInfo);

// Set checkbox form field properties
let dropdownfieldInfo: DropDownFormFieldInfo = documentEditor.getFormFieldInfo('Drop1') as DropDownFormFieldInfo;
dropdownfieldInfo.dropDownItems = ['One','Two', 'Three']
documentEditor.setFormFieldInfo('Drop1',dropdownfieldInfo);
```

## Export form field data

Data of the all the Form fields in the document can be exported using [`exportFormData`](../api/document-editor/#exportformdata).

```typescript
let formFieldDate: FormFieldData[] = documentEditor.exportFormData();
```

## Import form field data

Form fields can be prefilled with data using [`importFormData`](../api/document-editor/#importformdata).

```typescript
let textformField: FormFieldData = {fieldName: 'Text1', value: 'Hello World'};
let checkformField: FormFieldData = {fieldName: 'Check1', value: true};
let dropdownformField: FormFieldData = {fieldName: 'Drop1', value: 1};
//Import form field data
this.container.documentEditor.importFormData([textformField,checkformField,dropdownformField]);
```

## Reset form fields

Reset all the form fields in current document to default value using [`resetFormFields`](../api/document-editor/#resetformfields).

```typescript
documentEditor.resetFormFields();
```
