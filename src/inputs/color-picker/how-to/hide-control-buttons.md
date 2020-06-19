# Hide control buttons

Color Picker can be rendered without control buttons (Apply/Cancel). In this case, while selecting a color, the
Color Picker pop-up is closed and selected color can be applied directly. To hide control buttons, set the [`ShowButtons`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Inputs.SfColorPicker~ShowButtons.html) property to `false`.

```csharp
@using Syncfusion.Blazor.Inputs

<h4>Choose a color</h4>
<SfColorPicker ShowButtons="false"></SfColorPicker>
```

Output be like
![color-picker](./../images/hide-control.png)