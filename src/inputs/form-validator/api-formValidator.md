# FormValidator

FormValidator class enables you to validate the form fields based on your defined rules
```html
<form id='formId'>
 <input type='text' name='Name' />
 <input type='text' name='Age' />
</form>
<script>
  let formObject = new FormValidator('#formId', {
     rules: { Name: { required: true }, Age: { range: [18, 30] } };
  });
  formObject.validate();
</script>
```

## Properties

### errorClass `string`

Sets the defined css class to error fields

Defaults to *'e-error';*

### errorContainer `string`

Specify HTML element for error container

Defaults to *: 'div';*

### errorElement `string`

Specify HTML element for error

Defaults to *: 'label';*

### errorOption [`ErrorOption`](./api-errorOption.html)

Option to display the error

Defaults to *: ErrorOption.Label;*

### ignore `string`

Ignores input fields based on the class name

Defaults to *'e-hidden';*

### rules ``Object``

Maps the input fields with validation rules

Defaults to *{};*

### validClass `string`

Sets the defined css class to valid fields

Defaults to *: 'e-valid';*

## Methods

### addEventListener

Adds the handler to the given event listener.

Returns *void*

### addRules

Add validation rules to the corresponding input element based on `name` attribute.

| Parameter | Type | Description |
|------|------|-------------|
| name |  `string` | `name` of form field. |
| rules |  `Object` | Validation rules for the corresponding element. |

Returns *void*

### dataBind

Bind property changes immediately to components

Returns *void*

### destroy

Destroy the form validator object and error elements.

Returns *void*

### getInputElement

Get input element by name.

| Parameter | Type | Description |
|------|------|-------------|
| name |  `string` | Input element name attribute value. |

Returns *HTMLInputElement*

### removeEventListener

Removes the handler from the given event listener.

Returns *void*

### removeRules

Remove validation to the corresponding field based on name attribute.
When no parameter is passed, remove all the validations in the form.

| Parameter | Type | Description |
|------|------|-------------|
| name (*optional*) |  `string` | Input name attribute value. |
| rules (*optional*) |  `string[]` | List of validation rules need to be remove from the corresponding element. |

Returns *void*

### reset

Reset the value of all the fields in form.

Returns *void*

### validate

Validate the current form values using defined rules.
Returns `true` when the form is valid otherwise `false`

| Parameter | Type | Description |
|------|------|-------------|
| selected (*optional*) |  `string` | Optional parameter to validate specified element. |

Returns *boolean*

## Events

### change  `EmitType<Event>`

Trigger when a select/drop-down field is changed

### click  `EmitType<Event>`

Triggers when a check box field is clicked

### customPlacement  `EmitType<Object>`

Assigns the custom function to place the error message in the page.

### focusout  `EmitType<Event>`

Triggers when a field's focused  out

### keyup  `EmitType<KeyboardEvent>`

Trigger when keyup is triggered in any fields

### submit  `EmitType<Event>`

Triggers before form is being submitted

### validationBegin  `EmitType<Object>`

Triggers before validation starts

### validationComplete  `EmitType<Object>`

Triggers after validation is completed
