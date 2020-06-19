---
title: "Blazor Rich Text Editor | Image handling with upload"
component: "Rich Text Editor"
description: "This section explains how to handle images in the Blazor Rich Text Editor with upload image from local and server, the image resizes, an image with a link, and more."
---

# Image

Rich Text Editor allows inserting images from online sources and local computer where you want to insert the image in your content. For inserting the image to the Rich Text Editor, the following list of options have been provided in the `RichTextEditorImageSettings`.

| Options | Description |
|----------------|---------|
| AllowedTypes | Specifies the extensions of the image types allowed to insert on bowering and passing the extensions with comma separators. For example, pass allowedTypes as .jpg and .png.|
| Display | Sets the default display for an image when it is inserted in to the Rich Text Editor. Possible options are: `inline` and `break`.|
| Width | Sets the default width of the image when it is inserted in the Rich Text Editor.|
| Height | Sets the default height of the image when it is inserted in the Rich Text Editor.|
| SaveUrl | Provides URL to map the action result method to save the image.|
| Path | Specifies the location to store the image.|
| Resize | Enables resizing for image element.|
| MinWidth | Defines the maximum Width of the image.|
| MaxWidth | Defines the maximum Width of the image.|
| MinHeight | Defines the minimum Height of the image.|
| MaxHeight | Defines the maximum Height of the image.|
| ResizeByPercent | Image resizing should be done by percentage calculation.|

## Upload options

Through the `browse` option in the Image dialog, select the image from the local machine and insert into the Rich Text Editor content.

If the path field is not specified in the `RichTextEditorImageSettings`, the image will be converted into base 64 and blob url for the image will be created and the generated url will be set as src property of `<img>` tag as below.

The image has been loaded from the local machine and it will be saved in the given location.

```bash

<img src="blob:http://blazor.syncfusion.com/3ab56a6e-ec0d-490f-85a5-f0aeb0ad8879" >

```

> If you want to insert a lot of tiny images in the editor and don't want a specific physical location for saving images, you can opt to save format as Base64.

## Server side action

The selected image can be uploaded to the required destination by using the following controller action. Map this method name in `SaveUrl` property of `RichTextEditorImageSettings` and provide required destination path through `Path` property.

> The following code block shows saving the image file uploaded to Rich Text Editor using the `Blazor(ASP.NET Core Hosted)` project.

`Index.razor`

```csharp

<SfRichTextEditor>
    <RichTextEditorImageSettings SaveUrl="/api/SampleData/SaveFile" Path="../Images/"></RichTextEditorImageSettings>
    <p>Rich Text Editor allows to insert images from online source as well as local computer where you want to insert the image in your content.</p>
    <p><b>Get started Quick Toolbar to click on the image</b></p>
    <p>It is possible to add custom style on the selected image inside the Rich Text Editor through quick toolbar.</p>
    <img alt='Logo' style='width: 300px; height: 300px; transform: rotate(0deg);' src='https://blazor.syncfusion.com/demos/images/RichTextEditor/RTEImage-Feather.png' />
</SfRichTextEditor>

```

`HomeController.cs`

```csharp

[Route("api/[controller]")]
public class HomeController : Controller
{
    private IWebHostEnvironment hostingEnv;
    public HomeController(IWebHostEnvironment env)
    {
        hostingEnv = env;
    }
    public ActionResult Index()
    {
        return View();
    }

    [HttpPost("[action]")]
    public IActionResult SaveFile(IList<IFormFile> UploadFiles)
    {
        try
        {
            foreach (IFormFile file in UploadFiles)
            {
                if (UploadFiles != null)
                {
                    string filename = ContentDispositionHeaderValue.Parse(file.ContentDisposition).FileName.Trim('"');
                    if(!System.IO.Directory.Exists("Images"))
                    {
                        System.IO.Directory.CreateDirectory("Images");
                    }
                    //To save the image in the sever side
                    filename = hostingEnv.ContentRootPath + "\\Images" + $@"\{filename}";
                    if (!System.IO.File.Exists(filename))
                    {
                        using (FileStream fs = System.IO.File.Create(filename))
                        {
                            file.CopyTo(fs);
                            fs.Flush();
                        }
                    }
                    else
                    {
                        Response.Clear();
                        Response.StatusCode = 204;
                        Response.HttpContext.Features.Get<IHttpResponseFeature>().ReasonPhrase = "File already exists.";
                    }
                }
            }
        }
        catch (Exception e)
        {
            Response.Clear();
            Response.ContentType = "application/json; charset=utf-8";
            Response.StatusCode = 204;
            Response.HttpContext.Features.Get<IHttpResponseFeature>().ReasonPhrase = "No Content";
            Response.HttpContext.Features.Get<IHttpResponseFeature>().ReasonPhrase = e.Message;
        }
        return Content("");
    }
}

```

The output will be as follows.

![Image](./images/image-upload.png)

## Image delete

To remove am image from the Rich Text Editor content, select the image and click "Remove" tool from quick toolbar. It will delete the image from the Rich Text Editor content.

After selecting the image from the local machine, the URL for the image will be generated, from there also you can remove the image from the service location by clicking the cross icon as in the following image.

![RTE Image delete](./images/image-del.png)

## Insert from web

To insert an image from online source like Google, Ping, and more, enable images tool on the editor’s toolbar. By default, the images tool opens an image dialog that allows you to insert an image from online source.

![RTE Image insert](./images/image-web.png)

## Dimension

Sets the default width and height of the image when it is inserted in the Rich Text Editor using `Width` and `Height` of `RichTextEditorImageSettings`.

Through the `QuickToolbar` also you can change the width and height using `Change Size` option. After clicking the option, the image size will open as below. In that specify the width and height of the image in pixel.

![RTE Image dimension](./images/image-size.png)

## Caption and Alt Text

Image caption and alternative text can be specified for the inserted image in the Rich Text Editor using the `RichTextEditorQuickToolbarSettings` options such as Image Caption and Alternative Text.

Through the Alternative Text option, set the alternative text for the image, when the image is not uploaded successfully into the Rich Text Editor.

By clicking the Image Caption, the image will get wrapped in an image element with a caption. Then, you can type caption content inside the Rich Text Editor.

## Display position

Sets the default display for an image when it is inserted in the
Rich Text Editor using `Display` field in`RichTextEditorImageSettings`.

> It has two possible options: `Inline` and `Break`.

```csharp

@using Syncfusion.Blazor
@using Syncfusion.Blazor.RichTextEditor

<SfRichTextEditor>
    <RichTextEditorImageSettings Display="Inline"></RichTextEditorImageSettings>
    <p>Rich Text Editor allows to insert images from online source as well as local computer where you want to insert the image in your content.</p>
    <p><b>Get started Quick Toolbar to click on the image</b></p>
    <p>It is possible to add custom style on the selected image inside the Rich Text Editor through quick toolbar.</p>
    <img alt='Logo' style='width: 300px; height: 300px; transform: rotate(0deg);' src='https://blazor.syncfusion.com/demos/images/RichTextEditor/RTEImage-Feather.png' />
</SfRichTextEditor>

```

## Image with link

The hyperlink itself can be an image in Rich Text Editor. If the image given as hyperlink, the remove, edit, and open links will be added to the quick toolbar of image as below. For further details about link, refer to the [`link documentation`](./link).

![RTE image with link](./images/image-link.png)

## Resize

Rich Text Editor has a built-in image inserting support.  The resize points will be appearing on each corner of image when focus. So, users can resize the image using mouse points or thumb through the resize points easily. Also, the resize calculation will be done based on aspect ratio.

![RTE image resize](./images/image-resize.png)

## See Also

* [How to edit the quick toolbar settings](./toolbar/#quick-inline-toolbar)
* [How to use link editing option in the toolbar items](./link/)
