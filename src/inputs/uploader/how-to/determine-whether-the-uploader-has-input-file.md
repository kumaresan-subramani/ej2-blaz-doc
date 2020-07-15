---
title: "Determine whether the uploader has input file (required validation)"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Determine whether the uploader has input file (required validation)

By setting the **required** attribute to uploader input element, you can validate the input file that has any value in it.
In the following sample, set required attribute to the uploader input element and showcase the validation
failure message using the `data-required-message` attribute.

{% tab template="uploader/required", es5Template="require-validation", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { detach, createElement } from '@syncfusion/ej2-base';
import { FormValidator, Uploader } from '@syncfusion/ej2-inputs';
import { Dialog } from '@syncfusion/ej2-popups';

let dropElement = document.getElementsByClassName('dropUpload')[0];
// Initialize the uploader component
let uploadObj: Uploader = new Uploader({
    autoUpload: false,
    selected: onFileSelect,
    allowedExtensions: 'image/*',
    multiple: true,
    dropArea: dropElement,
});
uploadObj.appendTo('#fileupload');

document.getElementById('customBrowse').onclick = () => {
    document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
};
function onFileSelect(args: any): void {
    if (args.filesData.length > 0) {
        if (document.getElementsByClassName('upload-image').length > 0) {
            detach(document.getElementsByClassName('imgWrapper')[0]);
        }
        let imageTag = createElement('IMG', { className: 'upload-image', attrs: { 'alt': 'Image' } });
        let wrapper: HTMLElement = createElement('span', { className: 'imgWrapper' }) as HTMLElement;
        wrapper.appendChild(imageTag);
        let rootFile = document.getElementsByClassName('dropUpload')[0];
        rootFile.insertBefore(wrapper, rootFile.firstChild);
        readURL(wrapper, args.filesData[0]);
    }
    args.cancel = true;
}

function readURL(li: HTMLElement, args: any): void {
    let preview: HTMLImageElement = li.querySelector('.upload-image');
    let file: File = args.rawFile; let reader: FileReader = new FileReader();
    reader.addEventListener('load', () => { preview.src = reader.result; }, false);
    if (file) { reader.readAsDataURL(file); }
}

let options = {};
let formObj: FormValidator = new FormValidator('#form1', options);

function onFormSubmit(): void {
    let formStatus: Boolean = formObj.validate();
    if (formStatus) {
        formObj.element.reset();
        detach(document.getElementsByClassName('imgWrapper')[0]);
        confirm.show();
    }
}

let confirm: Dialog = new Dialog({
    width: '335px',
    visible: false,
    header: 'Success',
    content: 'Your details have been updated successfully, Thank you.',
    target: document.getElementById('control_wrapper'),
    showCloseIcon: true,
    isModal: true,
    animationSettings: {
        effect: 'Zoom'
    }
});
confirm.appendTo('#confirmationDialog');

document.getElementById('submit-btn').onclick = () => {
    onFormSubmit();
};
```

{% endtab %}