---
title: "Blazor Modal Dialog | Two-way binding to Visible property"
component: "Dialog"
description: "This section explains how to achieve two-way binding to visible property of Blazor Modal Dialog that helps to open or show the dialog dynamically."
---

# Achieve two-way binding to the visible property

## Two-way binding

The `Visible` property is enabled by default and has two-way binding capabilities in Blazor dialog. To prevent the dialog from showing on-page load, set the property to `false` using the `@bind-Visible` attribute.

Bind the `Visible` property as mentioned below to hide the dialog on-page load and show it on button-click.

```csharp

@using Syncfusion.Blazor.Popups
@using Syncfusion.Blazor.Buttons

<div class="col-lg-12 control-section" id="target">
    <SfButton @onclick="@OnBtnClick">Open Dialog</SfButton>
    <SfDialog Target="#target" Width="320px" @bind-Visible="@DialogVisible" ShowCloseIcon="true">
        <DialogTemplates>
            <Header> Update Required!!! </Header>
            <Content> Would you like to install the latest updates? </Content>
        </DialogTemplates>
        <DialogButtons>
             <DialogButton OnClick="@OnClicked">
                <DialogButtonModel Content="Update" IsPrimary="true"></DialogButtonModel>
            </DialogButton>
            <DialogButton OnClick="@OnClicked">
                <DialogButtonModel Content="Later"></DialogButtonModel>
            </DialogButton>
        </DialogButtons>
    </SfDialog>
</div>

<style>
    #target {
        min-height: 300px;
    }
</style>

@code {
    public bool DialogVisible { get; set; } = false;
    private void OnBtnClick()
    {
        this.DialogVisible = true;
    }
    private void OnClicked()
    {
         this.DialogVisible = false;
    }
}

```