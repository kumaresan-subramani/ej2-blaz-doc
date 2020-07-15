---
title: "Resize images before uploading it to the server"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Resize images before uploading it to the server

You can customize the dimension of the images before uploading it to the server.
By using selected event, you can get the selected file information as type of an object. From the obtained image file information, create a new canvas and render an image with the custom dimensions. Refer the corresponding code snippet as follows.

```html
<div id='upload'>
<!-- Initialize Uploader -->
    <input type='file' id='customUI' name='UploadFiles' />
</div>
<style>
.upload-success {color: #2bc700;}
#upload {
    width: 450px;
    margin: auto 400px;
}
.e-upload {
    width: 100%;
    margin-top: 50px;
}
.upload-list-root {
    display: inline-block;
    width: 450px;
}
.ul-element {
    list-style: none;
    padding-left: 0px;
    width: 100%;
}
.file-name-container {
    width: 100%;
}

.file-name {
    padding: 8px 6px 8px 4px;
    font-size:13px;
    width:100px;
    display: inline-block;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
    position: relative;
    top: 2px
}

.file-size {
    padding: 4px 0px;
    font-size: 13px;
    display: initial;
    position: relative;
    top: -8px;
}

.file-lists {
    border: 1px solid lightgray;
    padding: 0px 6px 0px 14px;
    margin-top: 15px;
    position: relative;
    background: rgba(0, 0, 0, 0.04);
}

span.file-status-container {
    padding: 10px 26px;
    font-size: 13px;
    position: relative;
    top: 0px;
    right: 60px;
    float: right;
}

.file-status-container, .file-size, .file-name {
    font-family: "Helvetica Neue", "Helvetica", "Arial", "sans-serif";
}
span.progress-bar-container {
    display: block;
    float: right;
    height: 20px;
    right: 50px;
    top: 11px;
    position: relative;
    right: 107px;
    width: 139px
}

.progress{
    width: 100%;
    height: 15px;
    -webkit-appearance: none;
}

.file-status-container {
    display: none;
}

.close-icon-container
{
    cursor: pointer;
    font-size: 11px;
    height: 24px;
    margin: 0 12px;
    padding: 0;
    position: absolute;
    right: 0;
    width: 24px;
    top: 8px;
}
.close-icon-container.e-icons::before {
    left: 6px;
    position: inherit;
    top: 6px;
    content: '\e932';
}

progress::-webkit-progress-bar {
    border: 1px solid lightgrey;
    background-color: #ffffff;
    border-radius: 2px;
}
progress::-webkit-progress-value {
    border-radius: 2px;
    background-color: skyblue;
}
</style>
```

```typescript

/**
 * Pre-resized image before upload
 */
import { Uploader, FileInfo } from '@syncfusion/ej2-inputs';
import { detach, isNullOrUndefined, createElement, EventHandler  } from '@syncfusion/ej2-base';

let uploadObj: Uploader = new Uploader({
    autoUpload: false,
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    allowedExtensions: 'image/*',
    selected: onFileSelect,
    progress : onFileUpload,
    success : onuploadSuccess,
    failure : onuploadFailed
});
uploadObj.appendTo('#customUI');

let newImage;
let parentElement : HTMLElement;
let ul: HTMLElement;
let proxy : any;

function onFileSelect(args : any) : void  {
    args.cancel = true;
    proxy = this;
    if ( isNullOrUndefined(document.getElementById('upload').querySelector('.upload-list-root'))) {
        parentElement = createElement('div', { className: 'upload-list-root' });
        ul = createElement('ul', {className: 'ul-element' });
        parentElement.appendChild(ul);
        document.getElementById('upload').appendChild(parentElement);
    }
    for (let i : number = 0; i < args.filesData.length; i++) {
        formSelectedData(args.filesData[i]);
    }
    this.filesData = this.filesData.concat(args.filesData);

    let file: FileInfo = args.filesData[0].rawFile;
    let width: number;
    let height: number;
    let img: any = document.createElement("img");
    let reader: any = new FileReader();
    reader.onload = function(e: any) { img.src = e.target.result; };
    reader.readAsDataURL(file);
    let imgs = new Image();
    img.onload = function() {
        width = this.width;
        height = this.height;
        onNewImg(height, width, img, args.filesData[0])
    }
    imgs.src = img.src;
}

    // to create canvas and update our custom dimensions
    function onNewImg(height: any, width: any, img: any, file: any) {
        let canvas: HTMLCanvasElement = document.createElement("canvas");
        let ctx: any = canvas.getContext("2d");
        ctx.drawImage(img, 0, 0);
        let MAX_WIDTH: any = 1000;
        let MAX_HEIGHT: any = 600;
        if (width > height) {
            if (width > MAX_WIDTH) {
                height *= MAX_WIDTH / width;
                width = MAX_WIDTH;
            }
        } else {
            if (height > MAX_HEIGHT) {
                width *= MAX_HEIGHT / height;
                height = MAX_HEIGHT;
            }
        }
        canvas.width = width;
        canvas.height = height;
        let ctx1 = canvas.getContext("2d");
        ctx1.drawImage(img, 0, 0, width, height);
        newImage = canvas.toDataURL("image/png");
        let blobBin = atob(newImage.split(',')[1]);
        let array = [];
        for(var i = 0; i < blobBin.length; i++) {
            array.push(blobBin.charCodeAt(i));
        }
        let newBlob = new Blob([new Uint8Array(array)], {type: 'image/png'});
        let newFile: any = createFile(newBlob, file);
        uploadObj.upload(newFile, true);
    }
    // To create File object to upload
    function createFile(image: any , file: any) {
        let newFile = {
            name: file.name,
            rawFile: image,
            size: image.size,
            type: file.type,
            validationMessage: '',
            statusCode: '1',
            status: 'Ready to Upload'
        }
        return newFile;
    }

function formSelectedData ( selectedFiles : FileInfo ) : void {
    let liEle : HTMLElement = createElement('li',  { className: 'file-lists', attrs: {'data-file-name' : selectedFiles.name} });
    let fileNameContainer : HTMLElement = createElement('span', {className: 'file-name-container' });
    let fileName : HTMLElement = createElement('span', {className: 'file-name ' });
    fileName.innerHTML = selectedFiles.name;
    let fileSize : HTMLElement = createElement('span', {className: 'file-size ' });
    fileSize.innerHTML = proxy.bytesToSize(selectedFiles.size);
    liEle.appendChild(fileName);
    liEle.appendChild(fileSize);
    let fileStatusContainer : HTMLElement = createElement('span', {className: 'file-status-container' });
    let fileStatus : HTMLElement = createElement('span', {className: 'file-status'});
    fileStatusContainer.appendChild(fileStatus);
    let progressbarContainer : HTMLElement = createElement('span', {className: 'progress-bar-container'});
    let progressBar : HTMLElement = createElement('progress', {className: 'progress', attrs: {value : '0', max : '100'}} );
    progressbarContainer.appendChild(progressBar);
    let closeIconContainer : HTMLElement = createElement('span', {className: 'e-icons close-icon-container'});
    EventHandler.add(closeIconContainer, 'click', removeFiles, proxy);
    liEle.appendChild(fileStatusContainer);
    liEle.appendChild(progressbarContainer);
    liEle.appendChild(closeIconContainer);
    ul.appendChild(liEle);
    proxy.fileList.push(liEle);
}

function onFileUpload(args : any) : void {
    let li : Element = document.getElementById('upload').querySelector('[data-file-name="' + args.file.name + '"]');
    let progressValue : number = Math.round((args.e.loaded / args.e.total) * 100);
    li.getElementsByTagName('progress')[0].value = progressValue;
}

function onuploadSuccess(args : any): void {
    let li : Element = document.getElementById('upload').querySelector('[data-file-name="' + args.file.name + '"]');
    if (!isNullOrUndefined(li.querySelector('.progress-bar-container'))) {
        detach(li.querySelector('.progress-bar-container'));
    }
    if (args.operation === 'upload') {
        li.querySelector('.file-status').classList.add('upload-success');
        li.querySelector('.file-status').innerHTML = args.file.status;
        li.querySelector('.file-status-container').setAttribute('style', 'display: inline-block');
    }
    if (args.operation === 'remove') {
        let index: number = this.fileList.indexOf(li);
        this.fileList.splice(index, 1);
        this.filesData.splice(index, 1);
        detach(li);
    }
}

function onuploadFailed(args : any): void {
    let li : Element = document.getElementById('upload').querySelector('[data-file-name="' + args.file.name + '"]');
    li.querySelector('.file-status').innerHTML = args.file.status;
    if (args.operation === 'upload') {
        detach(li.querySelector('.progress-bar-container'));
        li.querySelector('.file-status-container').setAttribute('style', 'display: initial');
    }
}

function removeFiles(args : any): void {
    let index: any = proxy.fileList.indexOf(args.currentTarget.parentElement);
    return proxy.remove(proxy.filesData[index]);
}

```