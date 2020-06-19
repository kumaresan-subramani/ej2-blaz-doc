---
title: "Blazor Modal Dialog | Changing the position using Draggable"
component: "Dialog"
description: "This section explains about draggable modal dialog which allows changing its position dynamically using drag-and-drop through its header."
---

# Draggable

The Dialog supports to `drag` within its target container by grabbing the Dialog header, which allows the user to reposition the Dialog dynamically.

```csharp

@using Syncfusion.Blazor
@using Syncfusion.Blazor.Popups
@using Syncfusion.Blazor.Buttons

<div id="target">
    <SfButton @onclick="@OnClicked">Open Dialog</SfButton>
    <SfDialog @bind-Visible="@IsVisible" Target="#target" Width="250px" AllowDragging="true" IsModal="true" ShowCloseIcon="true">
        <DialogTemplates>
            <Header> Dialog</Header>
            <Content> This is a Dialog with drag enabled</Content>
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
</div>

<style>
    #target {
        min-height: 400px;
        height: 100%;
        position: relative;
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
}

```