---
title: "Achieve invisible upload"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Achieve invisible upload

You can achieve the invisible upload feature by using the selected event in uploader component. Refer to the following example.

{% tab template="uploader/invisible", es5Template="invisible-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader, SelectedEventArgs } from '@syncfusion/ej2-inputs';
import { createElement } from '@syncfusion/ej2-base';

let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    selected : onupload,
    locale: 'en-US',
    allowedExtensions: '.png, .jpg, .jpeg'
});
uploadObj.appendTo('#fileupload')

function onupload(args: SelectedEventArgs){
    for(let i = 0; i< args.filesData.length ; i++){
        let liparentDiv = createElement('div',  { className: 'image-list'});
        let liImage = createElement('img',  { className: 'image'});
        liparentDiv.appendChild(liImage);
        readURL(liImage, args.filesData[i]);
        document.getElementById('preview').appendChild(liparentDiv);
    }
    args.cancel=true;
}

function readURL(liImage: HTMLElement, file: any) {
    let imgPreview: HTMLImageElement = liImage as HTMLImageElement;
    let imageFile: File = file.rawFile;
    let reader: FileReader = new FileReader();
    reader.addEventListener( 'load', () => {
        imgPreview.src = reader.result;
    }, false);
    if (imageFile) {
        reader.readAsDataURL(imageFile);
    }
};
```

{% endtab %}