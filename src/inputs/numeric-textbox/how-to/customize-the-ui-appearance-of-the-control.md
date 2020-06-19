# Customize the UI appearance of the component

You can change the appearance of the NumericTextBox by adding custom [CssClass](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor~Syncfusion.Blazor.Inputs.SfNumericTextBox%601~CssClass.html) to the component and enabling styles. Refer to the following example to change the appearance of the NumericTextBox.

```csharp
@using Syncfusion.Blazor.Inputs

<SfNumericTextBox TValue="int?" Value=10 CssClass="e-style" Placeholder="Enter value" FloatLabelType="@FloatLabelType.Always"></SfNumericTextBox>

<style>
    .e-numeric.e-style .e-control.e-numerictextbox {
        color: royalblue;
        font-size: xx-large;
        border: 0px;
    }

    .e-input-group.e-style.e-control-wrapper:not(.e-success):not(.e-warning):not(.e-error):not(.e-float-icon-left), .e-float-input.e-control-wrapper:hover:not(.e-success):not(.e-warning):not(.e-error):not(.e-disabled):not(.e-float-icon-left) {
        border-color: royalblue;
    }

    .e-control-wrapper.e-numeric.e-float-input.e-style .e-spin-down {
        color: royalblue;
    }

    .e-control-wrapper.e-numeric.e-float-input.e-style .e-float-line::before {
        background: royalblue;
    }

    .e-control-wrapper.e-numeric.e-float-input.e-style .e-float-line::after {
        background: royalblue;
    }

    .e-control-wrapper.e-numeric.e-float-input.e-style .e-spin-up {
        color: royalblue;
    }

    .e-control-wrapper.e-numeric.e-float-input.e-style.e-input-group .e-float-text.e-label-top {
        color: royalblue;
        font-size: medium;
    }
</style>
```

The output will be as follows.

![NumericTextBox Sample](../images/customization.png)
