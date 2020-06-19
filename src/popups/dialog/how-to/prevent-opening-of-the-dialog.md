---
title: "Blazor Modal Dialog | Prevent modal from opening"
component: "Dialog"
description: "This section explains how to prevent the Blazor Modal Dialog from opening, which helps to open the Modal Dialog with condition-based."
---

# Prevent opening of the dialog

You can prevent opening of  the dialog by setting the `OnOpen` event argument cancel value to true.
In the following sample, the success dialog is opened when you enter the username value with minimum 4 characters. Otherwise, it will not be opened.

```csharp

@using Syncfusion.Blazor
@using Syncfusion.Blazor.Popups

<div class="login-form">
    <div class='wrap'>
        <div id="heading">Sign in</div>
            <div id="input-container">
                <div class="e-float-input e-input-group">
                <input id="textvalue" type="text" @bind-value="@Textvalue" required />
                <span class="e-float-line"></span>
                <label class="e-float-text">Username</label>
            </div>
            <div class="e-float-input e-input-group">
                <input id="textvalue2" type="password" @bind-value="@Textvalue2" required />
                <span class="e-float-line"></span>
                <label class="e-float-text">Password</label>
            </div>
        </div>
        <div class="button-contain">
        <SfButton @onclick="@OnClicked">Log in</SfButton>
        </div>
    </div>
</div>
<SfDialog IsModal="true" Width="280px" @bind-Visible="@Visibility">
    <DialogEvents OnOpen="Validation" ></DialogEvents>
    <DialogTemplates>
        <Header> Success</Header>
        <Content> Congratulations! Login Success</Content>
    </DialogTemplates>
    <DialogButtons>
    <DialogButton OnClick="@OnClick">
        <DialogButtonModel Content="Dismiss" IsPrimary="true"></DialogButtonModel>
        </DialogButton>
    </DialogButtons>
</SfDialog>

<style>
    .wrap {
        box-sizing: border-box;
        margin: 0 auto;
        padding: 20px 30px;
        width: 340px;
        background: #f7f7f7;
    }
    #input-container .e-float-input { /* csslint allow: adjoining-classes */
        margin: 17px 0;
    }
    .wrap #input-container .e-control e-btn { /* csslint allow: adjoining-classes */
        margin: 3% 26%;
    }

    .button-contain {
        padding: 20px 0 0;
        width: 100%;
    }
    .button-contain .e-btn { /* csslint allow: adjoining-classes */
        width: 100%;
        height: 36px;
    }
    #heading {
        color: #333;
        font-weight: bold;
        margin: 0 0 15px;
        text-align: center;
        font-size: 20px;
    }
    .login-form {
        width: 340px;
        margin: 50px auto;
    }
    .e-dialog .e-footer-content {
        text-align: center;
    }
</style>

@code {  
    public bool Visibility { get;set; } = false;
    private string Textvalue { get; set; } = "";
    private string Textvalue2 { get; set; } = "";

    private void OnClick()
    {
        this.Visibility = false;
    }

    private void OnClicked()
    {
        this.Visibility = true;
    }

    private void Validation(BeforeOpenEventArgs args)
    {
        if (this.Textvalue == "" && this.Textvalue2 == "")
        {
            args.Cancel = true;
            Console.WriteLine("clicked");
        } else if (this.Textvalue == "") {
            args.Cancel= true;
            Console.WriteLine("Enter the username");
        } else if (this.Textvalue2 == "") {
            args.Cancel= true;
            Console.WriteLine("Enter the password");
        } else if (this.Textvalue.Length < 4) {
            args.Cancel= true;
            Console.WriteLine("Username must be minimum 4 characters");
        } else {
            args.Cancel= false;
            this.Textvalue = "";
            this.Textvalue2 = "";
        }
    }

```
