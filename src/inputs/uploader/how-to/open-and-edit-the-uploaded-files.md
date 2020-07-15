---
title: "Open and edit the uploaded files"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Open and edit the uploaded files

The uploader component allows you to modify the file after uploading to the server, which can be achieved
using the `success` event of the uploader.

You can retrieve the saved file path in the uploader success event and assign it to custom attribute (data-file-name) value of the respective file list element to open the uploaded file. Click the respective file element to create a new request along with saved file path using the HTTP header. In the server-side, get the file path from the header and open the file using `process.start` method.

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';


let uploadObj: any = new Uploader({
    asyncSettings: {
        saveUrl: 'SaveUrl',
        removeUrl: 'RemoveUrl'
    },
    success: onUploadSuccess
});
uploadObj.appendTo('#fileupload');

function onUploadSuccess(args) {
    // fetching the generated li elements
    var liElements = this.uploadWrapper.querySelectorAll('.e-upload-file-list');
    for (var i = 0; i < liElements.length; i++) {
        if (liElements[i].getAttribute('data-file-name') == args.file.name) {
            liElements[i].addEventListener('click', () => { openFile(args, event) })
            // File path have to update from server end in response status description.
            liElements[i].setAttribute('file-path', args.e.target.statusText);
        }
    }
}

function openFile(args, e) {
    if (!e.target.classList.contains('e-file-delete-btn') && !e.target.classList.contains('e-file-remove-btn'))
    {
        let ajax = new XMLHttpRequest();
        // create new request for open the selected file
        ajax.open("POST", '/Home/openFile');
        var liElements = document.getElementsByClassName('e-upload')[0].querySelectorAll('.e-upload-file-list');
        for (var i = 0; i < liElements.length; i++) {
            if (liElements[i].getAttribute('data-file-name') == args.file.name) {
                // Added the file path in header to get it in server side.
            ajax.setRequestHeader('filePath', liElements[i].getAttribute('file-path').toString());
            }
        }
        ajax.send();
    }
}
```

## Server side for open and edit the uploaded files

```csharp
public void Save() {
    if (!System.IO.File.Exists(fileSavePath))
    {
        httpPostedFile.SaveAs(fileSavePath);
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        // Sending the file path to client side
        Response.StatusDescription = fileSavePath;
        Response.End();
    }
}

[AcceptVerbs("Post")]
public void openFile()
{
    // Check whether the file is available in the corresponding location
    if (System.IO.File.Exists(Request.Headers.GetValues("filePath").First()))
    {
        // This will open the selected file from server location in desktop
        Process.Start(Request.Headers.GetValues("filePath").First());
    }
}
```