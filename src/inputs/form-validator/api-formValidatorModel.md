# FormValidatorModel

Interface for a class FormValidator

## Properties

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

### errorClass `string`

Sets the defined css class to error fields

### errorContainer `string`

Specify HTML element for error container

### errorElement `string`

Specify HTML element for error

### errorOption [`ErrorOption`](./api-errorOption.html)

Option to display the error

### ignore `string`

Ignores input fields based on the class name

### rules ``Object``

Maps the input fields with validation rules

### validClass `string`

Sets the defined css class to valid fields
