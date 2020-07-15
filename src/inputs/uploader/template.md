---
title: "Template"
component: "Uploader"
description: "Explains how to customize the file list with action buttons using a template that helps to design own user interface in the file upload control."
---

# Template

You can customize the default appearance of uploader using a template along with buttons.

## File list template

The [template](../api/uploader/#template) property is used to customize the default appearance of each file in the list. It can be represented as the HTML element or string. The selected or dropped files are displayed as per the template layout provided. The remove and progress bar action is handled using the corresponding events when the template is defined.

For example, you can display file type icon along with default UI elements.

{% tab template="uploader/custom-template", es5Template="cust-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript

import { Uploader, FileInfo, SelectedEventArgs } from '@syncfusion/ej2-inputs';
import { Event, detach } from '@syncfusion/ej2-base';

let uploadObj: Uploader = new Uploader({
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    template: "<span class='wrapper'><span class='icon sf-icon-${type}'></span><span class='name file-name'>${name}</span></span>" +
    "<span class='file-size-td file-size'>${size} bytes</span> <span class='e-icons e-file-remove-btn' title='Remove'></span> <br/> " +
    "<progress id='progressBar' class='progressbar' value='0' max='100'></progress> <span class='percent-td percent'></span>",
    dropArea: document.getElementById('dropArea'),
    progress: onFileUpload,
    selected: onSelect,
    success: onuploadSuccess,
    failure: onuploadFailed
});
uploadObj.appendTo('#fileupload');

document.getElementById('browse').onclick = function() {
    document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click();
    return false;
}
document.getElementById('clearbtn').onclick = () => {
        uploadObj.element.value = '';
        detach(document.getElementById('dropArea').querySelector('.e-upload-files'));
    };
function onFileUpload(args: any) {
    let li: HTMLElement = this.uploadWrapper.querySelector('[data-file-name="' + args.file.name + '"]');
    let progressValue: number = Math.round((args.e.loaded / args.e.total) * 100);
    li.getElementsByTagName('progress')[0].value = progressValue;
    li.getElementsByClassName('percent')[0].textContent = progressValue.toString() + " %";
}
function onuploadSuccess(args: any) {
    if (args.operation === 'remove') {
        let height: string = document.getElementById('dropArea').style.height;
        height = (parseInt(height) - 40) + 'px';
        document.getElementById('dropArea').style.height = height;
    } else {
        let li: HTMLElement = this.uploadWrapper.querySelector('[data-file-name="' + args.file.name + '"]');
        let progressBar: HTMLElement = li.getElementsByTagName('progress')[0];
        progressBar.classList.add('e-upload-success');
        li.getElementsByClassName('percent')[0].classList.add('e-upload-success');
        let height: string = document.getElementById('dropArea').style.height;
        document.getElementById('dropArea').style.height = parseInt(height) - 15 + 'px';
    }
}
function onuploadFailed(args: any) {
    let li: HTMLElement = this.uploadWrapper.querySelector('[data-file-name="' + args.file.name + '"]');
    let progressBar: HTMLElement = li.getElementsByTagName('progress')[0];
    progressBar.classList.add('e-upload-failed');
    li.getElementsByClassName('percent')[0].classList.add('e-upload-failed');
}
function onSelect(args: SelectedEventArgs) {
    let length: number = args.filesData.length;
    let height: string = document.getElementById('dropArea').style.height;
    height = parseInt(height) + (length * 55) + 'px';
    document.getElementById('dropArea').style.height = height;
}
```

{% endtab %}

## Custom template

You can design the own template by preventing the default file list including buttons. The [showFileList](../api/uploader/#showfilelist) property used to display whether the default file list or own file list
When you use custom template to upload or remove the files, pass the custom UI argument as true to call `upload`/`remove` public method as follows:

* UploaderObj.[upload](../api/uploader/#upload)(filesData, true);

* UploaderObj.[remove](../api/uploader/#remove)(filesData, true);

Refer to the following code sample.

{% tab template="uploader/custom-template", es5Template="cust-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { Uploader, FileInfo } from '@syncfusion/ej2-inputs';
import { createElement, isNullOrUndefined, detach, EventHandler } from '@syncfusion/ej2-base';

    enableRipple(true);
    let dropElement: HTMLElement = document.getElementsByClassName('control-fluid')[0] as HTMLElement; let filesDetails : FileInfo[] = [];
    let filesList: HTMLElement[] = [];
    let uploadObj: Uploader = new Uploader({
        asyncSettings: {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        }, dropArea: dropElement, selected: onFileSelect, progress: onFileUpload, success: onUploadSuccess,
        failure: onUploadFailed, removing: onFileRemove,
    });
    uploadObj.appendTo('#fileupload');
    document.getElementById('browse').onclick = () => {
        document.getElementsByClassName('e-file-select-wrap')[0].querySelector('button').click(); return false;
    };
    document.getElementById('clearbtn').onclick = () => {
        uploadObj.element.value = '';
        detach(document.getElementById('dropArea').querySelector('.upload-list-root')); filesDetails = []; filesList = [];
    };
    let parentElement : HTMLElement; let proxy : any; let progressbarContainer : HTMLElement;
    function onFileSelect(args : any) : void  {
        if (isNullOrUndefined(document.getElementById('dropArea').querySelector('.upload-list-root'))) {
            parentElement = createElement('div', { className: 'upload-list-root' });
            parentElement.appendChild(createElement('ul', {className: 'ul-element' }));
            document.getElementById('dropArea').appendChild(parentElement);
        }
        for (let i : number = 0; i < args.filesData.length; i++) { formSelectedData(args.filesData[i], this); }
        filesDetails = filesDetails.concat(args.filesData);
        this.upload(args.filesData, true); args.cancel = true;
    }
    function formSelectedData ( selectedFiles : FileInfo, proxy: any ) : void {
        let liEle : HTMLElement = createElement('li',  { className: 'file-lists', attrs: {'data-file-name' : selectedFiles.name} });
        liEle.appendChild(createElement('span', {className: 'file-name ', innerHTML: selectedFiles.name }));
        liEle.appendChild(createElement('span', {className: 'file-size ', innerHTML: proxy.bytesToSize(selectedFiles.size) }));
        if (selectedFiles.statusCode === '1') {
            progressbarContainer = createElement('span', {className: 'progress-bar-container'});
            progressbarContainer.appendChild(createElement('progress', {className: 'progress', attrs: {value : '0', max : '100'}} ));
            liEle.appendChild(progressbarContainer);
        } else { liEle.querySelector('.file-name').classList.add('upload-fails'); }
        let closeIconContainer : HTMLElement = createElement('span', {className: 'e-icons close-icon-container'});
        EventHandler.add(closeIconContainer, 'click', removeFiles, proxy);
        liEle.appendChild(closeIconContainer); document.querySelector('.ul-element').appendChild(liEle);
        filesList.push(liEle);
    }
    function onFileUpload(args : any) : void {
        let li : Element = document.getElementById('dropArea').querySelector('[data-file-name="' + args.file.name + '"]');
        EventHandler.remove(li.querySelector('.close-icon-container'), 'click', removeFiles);
        let progressValue : number = Math.round((args.e.loaded / args.e.total) * 100);
        if (!isNaN(progressValue)) { li.getElementsByTagName('progress')[0].value = progressValue; }
    }
    function onUploadSuccess(args : any) : void {
        let li : Element = document.getElementById('dropArea').querySelector('[data-file-name="' + args.file.name + '"]');
        if (!isNullOrUndefined(li.querySelector('.progress-bar-container'))) {
             detach(li.querySelector('.progress-bar-container')); }
        if (args.operation === 'upload') {
            li.querySelector('.file-name').classList.add('upload-success');
            li.querySelector('.close-icon-container').classList.add('delete-icon');
        }
        if (args.operation === 'remove') {
            filesList.splice(this.fileList.indexOf(li), 1); filesDetails.splice(this.fileList.indexOf(li), 1);
        }
        EventHandler.add(li.querySelector('.close-icon-container'), 'click', removeFiles, this);
    }
    function onUploadFailed(args : any) : void {
        let li : Element = document.getElementById('dropArea').querySelector('[data-file-name="' + args.file.name + '"]');
        EventHandler.add(li.querySelector('.close-icon-container'), 'click', removeFiles, this);
        li.querySelector('.file-name ').classList.add('upload-fails');
        if (args.operation === 'upload') {detach(li.querySelector('.progress-bar-container')); }
    }
    function removeFiles(args : any) : void {
        if (!isNullOrUndefined(args.currentTarget)) {
            if (filesDetails[filesList.indexOf(args.currentTarget.parentElement)].statusCode === '2' ) {
                this.remove(filesDetails[filesList.indexOf(args.currentTarget.parentElement)]);
                filesDetails.splice(filesList.indexOf(args.currentTarget.parentElement), 1);
            } else  { onFileRemove(args); }
        }
    }
    function onFileRemove(args: any) : void {
        if (!isNullOrUndefined(args.currentTarget)) {
            if (filesDetails[filesList.indexOf(args.currentTarget.parentElement)].statusCode !== '2') {
                detach(args.currentTarget.parentElement); filesList.splice(filesList.indexOf(args.currentTarget.parentElement), 1);
            }
        }
    }
```

{% endtab %}

## See Also

* [Customize progress bar](./how-to/customize-progressbar)
* [Customize button with HTML element](./how-to/customize-button-with-html-element)
* [Customize drop area](./how-to/hide-default-drop-area)
