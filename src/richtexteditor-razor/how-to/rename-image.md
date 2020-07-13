---
title: "Blazor Rich Text Editor | how to | Rename images before inserting"
component: "Rich Text Editor"
description: "This section explains how to rename images in server and get the updated name for the image in the Blazor Rich Text Editor component."
---

# Rename uploaded images in server before inserting it in the Rich Text Editor

By using the `RichTextEditorImageSettings` property, we can specify the server handler to upload and rename the selected image. Then we can bind the `OnImageUploadSuccess` event, to receive the modified file name from the server and update it in the Rich Text Editor's insert image dialog.

```csharp

@using Syncfusion.Blazor
@using Syncfusion.Blazor.RichTextEditor

<div class="control-section">
    <div>
        <SfRichTextEditor Value="@Value" >
             <RichTextEditorImageSettings SaveUrl="@SaveUrl" Path="@Path" ></RichTextEditorImageSettings>
            <RichTextEditorEvents OnImageUploadSuccess="OnImageUploadSuccess" ></RichTextEditorEvents>
            <RichTextEditorToolbarSettings items="@Tools"></RichTextEditorToolbarSettings>
        </SfRichTextEditor>
    </div>
</div>

@functions {
    private string Value { get; set; } = @"<p><p>The Rich Text Editor component is WYSIWYG ('what you see is what you get') editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p><p><b> Key features:</b></p><ul><li><p> Provides <b>IFRAME</b> and <b>DIV</b> modes </p></li><li><p> Capable of handling markdown editing.</p></li><li><p> Contains a modular library to load the necessary functionality on demand.</p></li><li><p> Provides a fully customizable toolbar.</p></li><li><p> Provides HTML view to edit the source directly for developers.</p></li><li><p> Supports third - party library integration.</p></li><li><p> Allows preview of modified content before saving it.</p></li></ul>";

    public static object[] Tools = new object[] {
        "Bold", "Italic", "Underline", "StrikeThrough",
        "FontName", "FontSize", "FontColor", "BackgroundColor",
        "LowerCase", "UpperCase", "|",
        "Formats", "Alignments", "OrderedList", "UnorderedList",
        "Outdent", "Indent", "|", "CreateTable",
        "CreateLink", "Image", "|", "ClearFormat", "Print",
        "SourceCode", "FullScreen", "|", "Undo", "Redo"
    };

    private string SaveUrl { get; set; } = "[SERVICE_HOSTED_PATH]/api/RichTextEditor/Rename";
    private string Path { get; set; } = "../Images/";

    public void OnImageUploadSuccess(Object arg) {
        // Access the renamed file here from the Resonse headers
    }
}

```

To configure the server-side handler in the Web API service, refer the below code.

```csharp
[AcceptVerbs("Post")]
public void Rename()
{
    try
    {
        var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
        imageFile = httpPostedFile.FileName;
        if (httpPostedFile != null)
        {
            var fileSave = System.Web.HttpContext.Current.Server.MapPath("~/Images");
            if (!Directory.Exists(fileSave))
            {
                Directory.CreateDirectory(fileSave);
            }
            var fileName = Path.GetFileName(httpPostedFile.FileName);
            var fileSavePath = Path.Combine(fileSave, fileName);
            while (System.IO.File.Exists(fileSavePath))
            {
                imageFile = "rteImage" + x + "-" + fileName;
                fileSavePath = Path.Combine(fileSave, imageFile);
                x++;
            }
            if (!System.IO.File.Exists(fileSavePath))
            {
                httpPostedFile.SaveAs(fileSavePath);
                HttpResponse Response = System.Web.HttpContext.Current.Response;
                Response.Clear();
                Response.Headers.Add("name", imageFile);
                Response.ContentType = "application/json; charset=utf-8";
                Response.StatusDescription = "File uploaded succesfully";
                Response.End();
            }
        }
    }
    catch (Exception e)
    {
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        Response.StatusCode = 204;
        Response.Status = "204 No Content";
        Response.StatusDescription = e.Message;
        Response.End();
    }
}

```
