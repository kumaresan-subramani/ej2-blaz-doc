---
title: "Images"
component: "DocumentEditor"
description: "Learn the supported image types in JavaScript document editor and how to insert, resize, format images."
---

# Images

Document editor supports common raster format images like PNG, BMP, JPEG, and GIF. You can insert an image file or online image in the document using the `insertImage()` method. Refer to the following sample code.

{% tab template="document-editor/image",es5Template="image" , sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Editor, Selection, ImageResizer, EditorHistory } from '@syncfusion/ej2-documenteditor';
import { Button } from '@syncfusion/ej2-buttons';
DocumentEditor.Inject(Editor, Selection, ImageResizer, EditorHistory);
let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false,
    enableEditor: true,
    enableSection: true,
    enableImageResizer: true,
    enableEditorHistory: true
});
documenteditor.appendTo('#DocumentEditor');
let insertPictureButton: Button = new Button();
insertPictureButton.appendTo('#insert-picture');
document.getElementById('insert-picture').addEventListener('click', () => {
    let pictureUpload: HTMLInputElement = document.getElementById("insertImageButton") as HTMLInputElement;
    pictureUpload.value = '';
    pictureUpload.click();
});
document.getElementById('insertImageButton').addEventListener('change', onInsertImage);
function onInsertImage(args: any): void {
    if (navigator.userAgent.match('Chrome') || navigator.userAgent.match('Firefox') || navigator.userAgent.match('Edge') || navigator.userAgent.match('MSIE') || navigator.userAgent.match('.NET')) {
        if (args.target.files[0]) {
            let path = args.target.files[0];
            let reader = new FileReader();
            reader.onload = function (frEvent: any) {
                let base64String = frEvent.target.result;
                let image = document.createElement('img');
                image.addEventListener('load', function () {
                    documenteditor.editor.insertImage(base64String, this.width, this.height);
                })
                image.src = base64String;
            };
            reader.readAsDataURL(path);
        }
        //Safari does not Support FileReader Class
    } else {
        let image = document.createElement('img');
        image.addEventListener('load', function () {
            documenteditor.editor.insertImage(args.target.value);
        })
        image.src = args.target.value;
    }
}
```

{% endtab %}

Image files will be internally converted to base64 string. Whereas, online images are preserved as URL.

## Image resizing

Document editor provides built-in image resizer that can be injected into your application based on the requirements. This allows you to resize the image by dragging the resizing points using mouse or touch interactions. This resizer appears as follows.

![Image](images/image.png)

## Changing size

Document editor expose API to get or set the size of the selected image. Refer to the following sample code.

```typescript
documenteditor.selection.imageFormat.width = 800;
documenteditor.selection.imageFormat.height = 800;
```

## See Also

* [Feature modules](../document-editor/feature-module/)
