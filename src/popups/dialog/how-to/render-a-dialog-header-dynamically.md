---
title: "Blazor Modal Dialog | Render popup without header"
component: "Dialog"
description: "This section explains how to render a simple popup using the Blazor Modal Dialog by hiding its header (without header)."
---

# Render a dialog header dynamically

By default, the dialog is rendered without header. You can update its header dynamically using the `Header` property.

> In the following code, the dialog header is rendered on a button click.

```csharp

@using Syncfusion.Blazor
@using Syncfusion.Blazor.Popups
@using Syncfusion.Blazor.Buttons

<SfButton @onclick="@OnBtnClick">Open Dialog</SfButton>
<SfButton @onclick="@OnBtnClick2">Render Dynamic Header</SfButton>
<SfDialog @bind-Visible="@IsVisible" Header="@Header" Width="250px">
    <DialogTemplates>
        <Content>This is a dialog without header</Content>
    </DialogTemplates>
    <DialogButtons>
        <DialogButton OnClick="@OnClick">
            <DialogButtonModel Content="OK" IsPrimary="true"></DialogButtonModel>
        </DialogButton>
        <DialogButton OnClick="@OnClick">
            <DialogButtonModel Content="Cancel"></DialogButtonModel>
        </DialogButton>
    </DialogButtons>
</SfDialog>

@code {
    private bool IsVisible { get; set; } = true;

    private string Header { get; set; }

    private void OnClick()
    {
        this.IsVisible = false;
    }
    private void OnBtnClick()
    {
        this.IsVisible = true;
    }
    private void OnBtnClick2() {
        this.Header = "Dynamic Header";
    }

```

The output will be as follows.

![dialog](../images/dialog-without-header.png)