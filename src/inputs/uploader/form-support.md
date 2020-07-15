---
title: "Forms Support"
component: "Uploader"
description: "Explains how to integrate the file upload control in an HTML form (synchronous mode) and submit a form with selected files."
---

# Forms Support (Synchronous Upload)

The Uploader component works with HTML form like default file input. The following configuration is must to make the Uploader work inside the form.

    *   `saveUrl` and `removeUrl` must be null.
    *   `autoUpload` must be disabled.
    *   `name` attribute must be added in input element.

The selected or dropped files are received as a collection in form action when the form is submitted. The form action handles
the server-side operations that manage the file upload process. When you reset the form, the file list and data will be cleared.

{% tab template="uploader/form-support", es5Template="formsupport-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { FormValidator } from '@syncfusion/ej2-inputs';
import { Uploader } from '@syncfusion/ej2-inputs';
import { Dialog } from '@syncfusion/ej2-popups';

/**
 * Uploader form support sample
 */

    let dropElement: HTMLElement = document.getElementsByClassName('control-fluid')[0] as HTMLElement;
    // Initialize the uploader component
    let uploadObj: Uploader = new Uploader({
        autoUpload: false,
        selected: onFileSelect,
        allowedExtensions: 'image/*',
        dropArea: dropElement
    });
    uploadObj.appendTo('#fileupload');

    document.getElementById('browse').onclick = () => {
        document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click(); return false;
    };
    function onFileSelect(args: any): void {
        let inputElement: HTMLInputElement  = document.getElementById('upload') as HTMLInputElement;
        inputElement.value = args.filesData[0].name;
    }

    let options: any  = {
        // Initialize the CustomPlacement.
        customPlacement: (inputElement: Element, errorElement: Element) => {
            inputElement = inputElement.closest('.form-group').querySelector('.error');
            inputElement.parentElement.appendChild(errorElement);
        },
        rules: {
            'Name': {
                required: true
            },
            'Email': {
                required: true
            },
            'upload': {
                required: true
            }
        }
    };

    let formObj: FormValidator = new FormValidator('#form1', options);

    function onFormSubmit(): void {
    let formStatus: Boolean = formObj.validate();
    if (formStatus) {
            formObj.element.reset();
            confirm.show();
        }
    }

    let confirm: Dialog = new Dialog({
        width: '335px',
        visible: false,
        content: 'Your details has been updated successfully, Thank you',
        target: document.getElementById('control_wrapper'),
        isModal: true,
        animationSettings: {
            effect: 'Zoom'
        }
    });
    confirm.appendTo('#confirmationDialog');

    document.getElementById('submit-btn').onclick = () => {
        onFormSubmit();
    };

    confirm.overlayClick = () => {
        confirm.hide();
    };

```

{% endtab %}
