---
title: "Blazor Modal Dialog | Close on document click"
component: "Dialog"
description: "This section explains how to customize the closing behavior of Blazor Modal Dialog such as close it while clicking on the document."
---

# Close dialog while click on outside of dialog

By default, dialog can be closed by pressing Esc key and clicking the close icon at the right of dialog header. It can also be closed by clicking outside of the dialog using hide method.
Set the `CloseOnEscape` property value to false to prevent closing of the dialog when pressing Esc key.

In the following code, dialog is closed when clicking outside the dialog area using `Hide` method.

```csharp
@using Syncfusion.Blazor
@using Syncfusion.Blazor.Popups
@using Syncfusion.Blazor.Buttons

<SfButton @onclick="@OnClicked">Open Dialog</SfButton>
<div id="target" @onclick="@TargetClicked">
    <SfDialog @bind-Visible="@IsVisible" Target="#target" Width="300px" ShowCloseIcon="true" CloseOnEscape="false">
        <DialogTemplates>
            <Header> Delete Multiple Items</Header>
            <Content> Are you sure you want to permanently delete all of these items? </Content>
        </DialogTemplates>
        <DialogButtons>
           <DialogButton OnClick="@OnClick">
                <DialogButtonModel Content="Yes" IsPrimary="true"></DialogButtonModel>
            </DialogButton>
            <DialogButton OnClick="@OnClick">
                <DialogButtonModel Content="No"></DialogButtonModel>
            </DialogButton>
        </DialogButtons>
    </SfDialog>
</div>

<style>
    #target {
        min-height: 450px;
        height: 100%;
    }
</style>

@code {
    private bool IsVisible { get; set; } = true;

    private void OnClick()
    {
        this.IsVisible = false;
    }
    private void OnClicked()
    {
        this.IsVisible = true;
    }
    private void TargetClicked()
    {
        this.IsVisible = false;
    }

```