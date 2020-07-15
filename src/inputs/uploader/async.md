---
title: "Asynchronous Upload"
component: "Uploader"
description: "Explains how to upload single or multiple files using asynchronous mode with auto-upload, preload, and additional HTTP headers."
---

# Asynchronous upload

The uploader component allows you to upload the files asynchronously. The upload process requires save and remove action URL to manage the upload process in the server.

    *   The save action is necessary to handle the upload operation
    *   The remove action is optional, can handle the removed files from server

>The name attribute must match the name of a parameter in the POST method. For more information, refer [hear](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/file-uploads?view=aspnetcore-3.1#match-name-attribute-value-to-parameter-name-of-post-method). The name attribute is automatically generated from the control’s ID property. If the name attribute to be different from the ID property, then you can use the htmlAttributes property to set the name attribute directly
to the input element. For more information refer [hear](./how-to/add-html-attributes).

The File can be uploaded automatically or manually. For more information, you can refer to the [Auto Upload](../api/uploader/#autoupload) section from the documentation.

## Multiple file upload

By Default, the uploader component allows you to select and upload multiple files simultaneously. The selected files are
organized in a list for every file selection until you clear it by clicking clear button that is shown in footer.
You can add the multiple attributes to original input element of file by enabling the multiple file selection.
The following example explains about [multiple](../api/uploader/#multiple) file upload settings.

In the following example, explains about multiple file upload settings.

{% tab template="uploader/multiple", es5Template="multiple-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    }
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Single file upload

You can select and upload a single file by disabling the multiple file selection property. The file list item is removed for every selection and it always maintain a single file to upload. You can remove the multiple attributes form the original input element of file by enabling the single file upload property.

The following example explains about single file upload settings.

{% tab template="uploader/single", es5Template="single-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    multiple: false
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Save Action

The save action handler upload the files that needs to be specified in the [saveUrl](../api/uploader/asyncSettingsModel/#saveurl) property.
The save handler receives the submitted files and manages the save process in server. After uploading the files to server location, the color of the selected file name changes to green and the remove icon is changed as bin icon.

    *   When the file is uploaded successfully, the event “success” triggers to handle the operation after upload.
    *   When the file is failed to upload, the event “failure” triggers with information, which cause this failure.

You can cancel the upload process by setting the upload event argument **eventargs.cancel** to true.

{% tab template="uploader/save", es5Template="save-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save'
    }
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

### Server-side configuration for save action

Here’s how to handle the server-side action for saving the file in server.

```csharp
[AcceptVerbs("Post")]
public void Save()
{
    try
    {
        if (HttpContext.Current.Request.Files.AllKeys.Length > 0)
        {
            var httpPostedFile = HttpContext.Current.Request.Files["UploadFiles"];

            if (httpPostedFile != null)
            {
                var fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
                var fileSavePath = Path.Combine(fileSave, httpPostedFile.FileName);
                if (!File.Exists(fileSavePath))
                {
                    httpPostedFile.SaveAs(fileSavePath);
                    HttpResponse Response = HttpContext.Current.Response;
                    Response.Clear();
                    Response.ContentType = "application/json; charset=utf-8";
                    Response.StatusDescription = "File uploaded succesfully";
                    Response.End();
                }
                else
                {
                    HttpResponse Response = HttpContext.Current.Response;
                    Response.Clear();
                    Response.Status = "400 File already exists";
                    Response.StatusCode = 400;
                    Response.StatusDescription = "File already exists";
                    Response.End();
                }
            }
        }
    }
    catch (Exception e)
    {
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        Response.StatusCode = 400;
        Response.Status = "400 No Content";
        Response.StatusDescription = e.Message;
        Response.End();
    }
}

```

## Remove Action

The remove action is optional. Specify the URL to handle remove process from server. The remove handler receives the posted files and handle the remove operation in server.

    *   When the files are removed successfully from server, the success event triggers to denote the process has completed.
    *   When remove action fails, the event “failure” triggers with information, which cause failure in remove process.

> You can differentiate the file operation whether the success event triggers from save or remove action in its arguments **eventArgs.operation**.

You can remove the files which is not uploaded locally by clicking the remove icon. In this case, the success or failure events will not be triggered.

{% tab template="uploader/remove", es5Template="remove-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    }
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

### Server-side configuration for remove action

Here’s how to handle the server-side action for removing the file from server.

```csharp
[AcceptVerbs("Post")]
public void Remove()
{
    try
    {
        var fileSave = "";
        if (HttpContext.Current.Request.Form["cancel-uploading"] != null)
        {
            fileSave = HttpContext.Current.Server.MapPath("UploadingFiles");
        }
        else
        {
            fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
        }
        var fileName = HttpContext.Current.Request.Files["UploadFiles"].FileName;
        var fileSavePath = Path.Combine(fileSave, fileName);
        if (File.Exists(fileSavePath))
        {
            File.Delete(fileSavePath);
        }
    }
    catch (Exception e)
    {
        HttpResponse Response = HttpContext.Current.Response;
        Response.Clear();
        Response.Status = "404 File not found";
        Response.StatusCode = 404;
        Response.StatusDescription = "File not found";
        Response.End();
    }
}

```

## Auto Upload

By default, the uploader processes the files to upload once the files are selected and added in upload queue. To upload manually, disable the [autoUpload](../api/uploader/#autoupload) &nbsp;property. When you disable this property, you can use the action buttons to call upload all or clear all actions manually. You can change those buttons text using the [buttons](../api/uploader/#buttons) &nbsp;property in the Uploader component.

{% tab template="uploader/auto-upload", es5Template="auto-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    // disable the auto upload functionalities
    autoUpload: false
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Sequential Upload

By default, the uploader control process multiple files to upload simultaneously. When you enable the [sequentialUpload](../api/uploader/#sequentialupload) property, the selected files will process sequentially (one after the other) to the server. If the file uploaded successfully or failed, the next file will upload automatically in this sequential upload. This feature helps to reduce the upload traffic and reduce the failure of file upload.

{% tab template="uploader/sequential-upload", es5Template="sequential-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    // enable the sequential upload functionality
    sequentialUpload: true
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Preload Files

The uploader component allows you to preload the list of files that are uploaded in the server. The preloaded files are useful to view and remove the files from server that can be achieved by the [files](../api/uploader/#files) property. By default, the files are configured with uploaded successfully state on rendering file list. By default, the files are configured with uploaded successfully state on rendering file list. The following properties are mandatory to configure the preloaded files:

    *   Name
    *   Size
    *   Type

{% tab template="uploader/preload-file", es5Template="preload-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader, FilesPropModel } from '@syncfusion/ej2-inputs';

let preLoadFiles: FilesPropModel[] = [
    {name: 'Books', size: 500, type: '.png'},
    {name: 'Movies', size: 12000, type: '.pdf'},
    {name: 'Study materials', size: 500000, type: '.docx'},
];
// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    files: preLoadFiles
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

## Adding additional HTTP headers with upload action

The Uploader component allows you to add the additional headers with `save` and `remove` action request using `uploading` and `removing` event, which helps to send validation token on file upload. Access the current request and set the request header within these events.

The following code block shows how to add the additional headers with save and remove action request.

```html
<div style='margin: auto 30%'>
    <input type='file' id='uploader' name="UploadFiles"/>
</div>

```

```typescript
import { Uploader} from '@syncfusion/ej2-inputs';

let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    uploading: addHeaders,
    removing: addHeaders
});
uploadObj.appendTo('#uploader')

function addHeaders(args: any) {
    args.currentRequest.setRequestHeader('custom-header', 'Syncfusion');
}

```

## See Also

* [How to add additional data on upload](./how-to/add-additional-data-on-upload)
* [How to add confirm dialog to remove the files](./how-to/add-confirm-dialog-to-remove-the-files)
* [Check the MIME type of file before uploading it](./how-to/check-the-mime-type-of-file-before-upload)
* [How to open and edit the uploaded files](./how-to/open-and-edit-the-uploaded-files)
