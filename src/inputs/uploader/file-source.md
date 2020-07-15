---
title: "File source"
component: "Uploader"
description: "Explains various sources to file upload such as drag and drop (customizable), paste the images, folder selection (directory upload)."
---

# File source

## Paste to upload

The uploader component allows you to upload the files using the select or drop files option from the file
explorer.  It also supports pasting to upload the image files. You can upload any currently copied images in the clipboard.

> When you paste the image, it will be saved in the server with the filename as `image.png`. The file name can
be renamed in the server end. You can generate a random name for the file name using `getUniqueID` method.
Refer to the following example.

{% tab template="uploader/auto-upload", es5Template="auto-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader, UploadingEventArgs } from '@syncfusion/ej2-inputs';
import { getUniqueID } from '@syncfusion/ej2-base';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    autoUpload: false,
    uploading: onUploadBegin
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');

function onUploadBegin(args: UploadingEventArgs): void {
    // check whether the file is uploading from paste.
    if (args.fileData.fileSource === 'paste') {
        let newName: string = getUniqueID(args.fileData.name.substring(0, args.fileData.name.lastIndexOf('.'))) + '.png';
        args.customFormData = [{'fileName': newName}];
    }
}
```

{% endtab %}

### Save action for paste to upload

```csharp
public void Save() {
    var httpPostedFile = HttpContext.Current.Request.Files["UploadFiles"];
    var fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
    var fileSavePath = Path.Combine(fileSave, httpPostedFile.FileName);
    if (!System.IO.File.Exists(fileSavePath))
    {
        httpPostedFile.SaveAs(fileSavePath);
        // Get the current file name
        var oldName = httpPostedFile.FileName;
        // Get the additional data as name in server end by corresponding key.
        var newName = HttpContext.Current.Request.Form["fileName"];
        // Rename the file
        File.Move(oldName, newName);
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        // Sending the file path to client side
        Response.StatusDescription = fileSavePath;
        Response.End();
    }
}
```

## Directory upload

The uploader component allows you to upload all files in the folders to server by using the [directoryUpload](../api/uploader/#directoryupload) property.
When this property is enabled, the uploader component processes the files by iterating through the files and
sub-directories in a directory. It allows you to select only folders instead of files to upload.

> The directory upload is available only in browsers that supports **HTML5 directory**. The uploader will
process directory upload by dragging and dropping in the Edge browser.
Refer to the following example to upload files to the server.

{% tab template="uploader/directory", es5Template="directory", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    directoryUpload: true
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

### Save action for directory upload

```csharp
public void Save() {
    var httpPostedFile = HttpContext.Current.Request.Files["UploadFiles"];
    var fileSave = HttpContext.Current.Server.MapPath("UploadedFiles");
    // split the folders by using file name
    string[] folders = httpPostedFile.FileName.Split('/');
    string fileSavePath = "";
    if (folders.Length > 1)
    {
        for (var i = 0; i < folders.Length - 1; i++)
        {
            var newFolder = Path.Combine(fileSave, folders[i]);
            // create folder
            Directory.CreateDirectory(newFolder);
            fileSave = newFolder;
        }
        fileSavePath = Path.Combine(fileSave, folders[folders.Length - 1]);
    }
    else
    {
        fileSavePath = Path.Combine(fileSave, httpPostedFile.FileName);
    }
    if (!System.IO.File.Exists(fileSavePath))
    {
        // save file in the corresponding server location
        httpPostedFile.SaveAs(fileSavePath);
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        // Sending the file path to client side
        Response.StatusDescription = fileSavePath;
        Response.End();
    }
}
```

## Drag and drop

The uploader component allows you to drag and drop the files to upload. You can drag the files from file explorer and drop into the drop area. By default, the uploader component act as drop area element. The drop area gets highlighted when you drag the files over drop area.

### Custom drop area

The uploader component allows you to set external target element as drop area using the [dropArea](../api/uploader/#droparea) property. The element can be represented as HTML element or element’s id.

{% tab template="uploader/drop-area", es5Template="customdrop-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    autoUpload: false,
    dropArea: document.getElementById('droparea')
});

// render initialized Uploader
uploadObject.appendTo('#fileupload');
```

{% endtab %}

### Customize drop area

You can customize the appearance of drop area by overriding the default drop area styles. The class “” and “” is available to handle this customization.

{% tab template="uploader/customize-drop", es5Template="customize-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';
// initialize Uploader component
let uploadObject: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    dropArea: document.getElementById('droparea')
});
// render initialized Uploader
uploadObject.appendTo('#fileupload');

document.getElementById('browse').onclick = function() {
    document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
    return false;
}
```

{% endtab %}

## See Also

* [Achieve file upload programmatically](./how-to/achieve-file-upload-programmatically)
* [Validate image/* on drop](./how-to/validate-image-on-drop)
