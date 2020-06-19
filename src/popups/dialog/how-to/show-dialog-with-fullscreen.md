---
title: "Blazor Modal Dialog | Render fullscreen modal"
component: "Dialog"
description: "This section explains how to render a fullscreen modal using the Blazor Dialog by extending its scale 100% to the document's width and height."
---

# Show dialog with fullscreen

You can show the dialog in fullscreen by passing `true` as argument to the dialog `Show` method. By using `Visible` property you can prevent the dialog from showing initially.

```csharp

@using Syncfusion.Blazor
@using Syncfusion.Blazor.Popups
@using Syncfusion.Blazor.Buttons

<SfButton @onclick="@OnBtnClick">Open</SfButton>
<SfDialog @ref="@dialogObj" Width="250px" ShowCloseIcon="true" @bind-Visible="@isVisible">
    <DialogTemplates>
        <Header> Dialog</Header>
        <Content> This is a Dialog with button and primary button</Content>
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
    private SfDialog dialogObj;
    private bool isVisible { get; set; } = false;
    private void OnClick()
    {
        this.isVisible = false;
    }

    private void OnBtnClick()
    {
        this.dialogObj.Show(true);
    }
}

```