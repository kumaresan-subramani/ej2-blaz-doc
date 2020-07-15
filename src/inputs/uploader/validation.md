---
title: "Validation"
component: "Uploader"
description: "Explains how to validate files before uploading it to a server such as valid file extensions, min and max file size, and duplicate files."
---

# Validation

The uploader component validate the selected files size and extension using the [allowedExtentions](../api/uploader/#allowedextensions), [minFileSize](../api/uploader/#minfilesize) and [maxFileSize](../api/uploader/#maxfilesize) properties. The files can be validated before uploading to the server and can be ignored on uploading. Also, you can validate the files by setting the HTML attributes to the original input element. The validation process occurs on drag-and-drop the files also.

## File type

You can allow the specific files alone to upload using the [allowedExtentions](../api/uploader/#allowedextensions) property. The extension can be represented as collection by comma separators. The uploader component filters the selected or dropped files to match against the specified file types and processes the upload operation. The validation happens when you specify value to inline attribute to accept the original input element.

{% tab template="uploader/type-validation", es5Template="type-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

// initialize Uploader component
    let uploadObj: Uploader = new Uploader({
        asyncSettings: {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        },
        allowedExtensions: '.jpg,.png'
    });
    uploadObj.appendTo('#fileupload');
```

{% endtab %}

## File size

The uploader component allows you to validate the files based on its size. The validation helps to restrict uploading large files or empty files to the server. The size can be represented in `bytes`. By default, the uploader component allows you to upload **minimum file size** as 0 byte and **maximum file size** as 28.4 MB using using the [minFileSize](../api/uploader/#minfilesize) and [maxFileSize](../api/uploader/#maxfilesize) properties.

{% tab template="uploader/size-validation", es5Template="size-template", sourceFiles="app.ts,index.html" %}

```typescript
import { Uploader  } from '@syncfusion/ej2-inputs';

    // Initialize the uploader component
    let uploadObj: Uploader = new Uploader({
        asyncSettings: {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        },
        minFileSize: 10000,
        maxFileSize: 1500000
    });
    uploadObj.appendTo('#fileupload');
```

{% endtab %}

## Maximum files count

You can restrict uploading the maximum number of files using the **selected** event. In the selected event arguments, you can get the currently selected files details using the `getFilesData()`. You can modify the files details and assign the modified file list to the `eventArgs.modifiedFilesData`.

{% tab template="uploader/max-count-validation", es5Template="filecount-template", sourceFiles="app.ts,index.html" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { Uploader, FileInfo, SelectedEventArgs } from '@syncfusion/ej2-inputs';
import { detach } from '@syncfusion/ej2-base';
import { createSpinner, showSpinner, hideSpinner } from '@syncfusion/ej2-popups';

enableRipple(true);
 let dropElement: HTMLElement = document.getElementsByClassName('control-fluid')[0] as HTMLElement;

    // Initialize the control with file validation
    let uploadObj: Uploader = new Uploader({
        autoUpload: false,
        minFileSize: 10000,
        allowedExtensions: '.doc, .docx, .xls, .xlsx',
        asyncSettings: {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        },
        selected: onFileSelected,
        success: onUploadSuccess,
        dropArea: dropElement
    });
    uploadObj.appendTo('#validation');

    function onFileSelected(args : SelectedEventArgs) : void {
        // Filter the 5 files only to showcase
        args.filesData.splice(5);
        let filesData : FileInfo[] = uploadObj.getFilesData();
        let allFiles : FileInfo[] = filesData.concat(args.filesData);
        if (allFiles.length > 5) {
            for (let i : number = 0; i < allFiles.length; i++) {
                if (allFiles.length > 5) {
                    allFiles.shift();
                }
            }
            args.filesData = allFiles;
            // set the modified custom data
            args.modifiedFilesData = args.filesData;
        }
        args.isModified = true;
    }

    function onUploadSuccess(args: any): void {
        let li: HTMLElement = this.uploadWrapper.querySelector('[data-file-name="' + args.file.name + '"]');
        if (args.operation === 'upload') {
            (li.querySelector('.e-file-delete-btn') as HTMLElement).onclick = () => {
                generateSpinner(this.uploadWrapper);
            };
            (li.querySelector('.e-file-delete-btn') as HTMLElement).onkeydown = (e: any) => {
                if (e.keyCode === 13) {
                    generateSpinner(e.target.closest('.e-upload'));
                }
            };
        } else {
            hideSpinner(this.uploadWrapper);
            detach(this.uploadWrapper.querySelector('.e-spinner-pane'));
        }
    }

    function generateSpinner(targetElement: HTMLElement): void {
        createSpinner({ target: targetElement, width: '25px' });
        showSpinner(targetElement);
    }

```

{% endtab %}

## Duplicate files

You can validate the duplicate files before uploading to server using the selected event. Compare the selected files with the existing files data and filter the file list by removing the duplicate files.

{% tab template="uploader/duplicate-file-validation", es5Template="duplicate-template", sourceFiles="app.ts,index.html" %}

```typescript
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { Uploader, FileInfo } from '@syncfusion/ej2-inputs';
import { detach, isNullOrUndefined } from '@syncfusion/ej2-base';

    // Initialize the control with file validation
     let uploadObj: Uploader = new Uploader({
        autoUpload: false,
        asyncSettings: {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        },
        selected: onFileSelect,
    });
    uploadObj.appendTo('#validation');

  function onFileSelect(args : any) {
    let existingFiles: FileInfo[] = this.getFilesData();
    for (let i: number = 0; i < args.filesData.length; i++) {
        for(let j: number = 0; j < existingFiles.length; j++) {
            if (!isNullOrUndefined(args.filesData[i])) {
                if (existingFiles[j].name == args.filesData[i].name) {
                    args.filesData.splice(i, 1);
                }
            }
        }
    }
    existingFiles = existingFiles.concat(args.filesData);
    args.modifiedFilesData = existingFiles;
    args.isModified = true;
}
```

{% endtab %}

## See Also

* [Validate image/* on drop](./how-to/validate-image-on-drop)
* [Determine whether uploader has file input (required validation)](./how-to/determine-whether-the-uploader-has-input-file)
* [Check file size before uploading it](./how-to/check-file-size-before-uploading)
* [Check the MIME type of file before uploading it](./how-to/check-the-mime-type-of-file-before-upload)
