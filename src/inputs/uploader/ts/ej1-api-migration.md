---
title: "Migration from Essential JS 1"
component: "Uploader"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, file upload component."
---

# Migration from Essential JS 1

This article describes the API migration process of File Upload component from Essential JS 1 to Essential JS 2.

## Accessibility

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Localization
</td>
<td>
<b>property</b>: locale
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
     locale: 'es-ES'
<br/>})
</td>
<td>
<b>property:</b> locale
<br/><br/>let uploader =new Uploader({<br/>
    locale: 'es-ES'
<br/>})<br/>
uploader.appendTo('#ej2_Uploader')
</td>
</tr>
<tr>
<td>
Right to left
</td>
<td>
<b>property:</b> enableRTL
<br/><br/>$('#uploadBox'). ejUploadbox({<br/>
     enableRTL: true
<br/>})<br/>
uploader.appendTo('#ej2_Uploader')
</td>
<td>
<b>property:</b> enableRtl
<br/><br/>let uploader =new Uploader({<br/>
    enableRtl: true
<br/>})<br/>
uploader.appendTo('#ej2_Uploader')
</td>
</tr>
</table>

## File list

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior</b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Show/Hide the selected files
</td>
<td>
<b>property</b>: showFileDetails
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  showFileDetails: false
<br/>})
</td>
<td>
<b>property</b>:  showFileList
<br/><br/>let uploader =new Uploader({<br/>
    showFileList: false
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
</td>
</tr>
<tr>
<td>
Customizing the file list
</td>
<td>
Not Applicable

</td>
<td>
<b>property</b>: template
<br/><br/>let uploader =new Uploader({<br/>
    template: '#templateId'
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')

</td>
</tr>
<tr>
<td>
Get the files in sorted form
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b>sortFileList
<br/><br/>let uploader =new Uploader()
<br/>uploader.appendTo('#ej2_Uploader')
<br/>
uploader.sortFileList(files)

</td>
</tr>
<tr>
<td>
Clearing File List
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b>clearAll
<br/><br/>let uploader =new Uploader()
<br/>uploader.appendTo('#ej2_Uploader')<br/>
uploader.clearAll()
</td>
</tr>
<tr>
<td>
Event triggers when clearing Files
</td>
<td>
Not Applicable
</td>
<td>
<b>Event :</b>clearing
<br/><br/>let uploader =new Uploader({<br/>
clearing: function() {}
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')

</td>
</tr>
</table>

## File selection

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
API in Essential JS 1
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Select multiple files to upload
</td>
<td>
<b>property</b>: multipleFilesSelection
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  multipleFilesSelection: true
<br/>})

</td>
<td>
<b>property</b>: multiple
<br/><br/>let uploader =new Uploader({<br/>
  multiple: true
<br/>})
<br/>uploader.appendTo('ej2_uploadbox')
</td>
</tr>
<tr>
<td>
Set minimum file size to upload
</td>
<td>
Not Applicable
</td>
<td>
<b>property</b>: minFileSize
<br/><br/>let uploader =new Uploader({<br/>
  minFileSize:  1024
<br/>})
<br/>uploader.appendTo('ej2_uploadbox')

</td>
</tr>
<tr>
<td>
Set maximum file size to upload
</td>
<td>
<b>property</b>: fileSize
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  fileSize: 5000
<br/>})
</td>
<td>
<b>property</b>: maxFileSize
<br/><br/>let uploader =new Uploader({<br/>
  maxFileSize:  5000
<br/>})
<br/>uploader.appendTo('ej2_uploadbox')

</td>
</tr>
<tr>
<td>
Allowed file types to select
</td>
<td>
<b>property</b>:  extensionsAllow
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
 extensionsAllow: '.zip'
<br/>})
</td>
<td>
<b>property:</b>allowedExtensions
<br/><br/>let uploader =new Uploader({<br/>
   allowedExtensions: '.pdf'
<br/>})
<br/>uploader.appendTo('ej2_uploadbox')

</td>
</tr>
<tr>
<td>
Restricted files types to select
</td>
<td>
<b>property:</b>extensionsDeny
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  extensionsDeny: '.docx'
<br/>})
</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Display only selected details in File list
</td>
<td>
<b>property</b>:  customFileDetails
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  customFileDetails:  {
     title: false,
     name: true,
     size: true,
     status: true,
     action: false
   }
<br/>})
</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Options to customize File list dialog
</td>
<td>
<b>property:</b>dialogAction
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
 dialogAction: {
   modal: false,
    closeOnComplete: true,
    resize: true,
    drag: false,
    content: '#dialogTarget'
   }
<br/>})
</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Customize dialog position
</td>
<td>
<b>property:</b>dialogPosition
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
   dialogPosition:  {X: 300, Y 100}
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Change file list key values
</td>
<td>
<b>property:</b>dialogText
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
   dialogText:  {
     title: 'Upload File List',
     name: 'File Name',
     size: 'File Size'
   }
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Change drop area text
</td>
<td>
<b>property:</b>dropAreaText
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  dropAreaText: 'Drop files here'
<br/>})

</td>
<td>
No separate property to change dropAreaText.
It can be customize using locale Texts
</td>
</tr>
<tr>
<td>
Change drop area height
</td>
<td>
<b>property:</b>dropAreaHeight
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  dropAreaHeight:  '100%'
<br/>})
</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Change drop area width
</td>
<td>
<b>property:</b>dropAreaWidth
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  dropAreaWidth:  '100%'
<br/>})
</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Dynamically push the file
</td>
<td>
<b>property:</b>pushFile
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
   pushFile: files
<br/>})
</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Show the files uploader in server already.
</td>
<td>
Not Applicable
</td>
<td>
<b>property:</b>files<br/>
let preloadFiles = [{ name: 'nature', size: 5000, type: '.png' }]
<br/>
let upload =new Uploader({<br/>
  files: preloadFiles
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')
</td>
</tr>
<tr>
<td>
Event triggers when select the file successfully
</td>
<td>
<b>Event:</b>fileSelect
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  fileSelect: function() {}
<br/>})
</td>
<td>
<b>Event:</b>selected <br/>
let upload =new Uploader({<br/>
 selected: onFileSelect
<br/>})
<br/>
upload.appendTo('#ej2_uploadBox')
function onFileSelect() {}
</td>
</tr>
</table>

## Upload action

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Save URL
</td>
<td>
<b>property</b>: saveUrl
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  saveUrl: 'saveUrl'
<br/>})
</td>
<td>
<b>property</b>: asyncSettings.saveUrl
<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'saveUrl'
}
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')

</td>
</tr>
<tr>
<td>
Remove URL
</td>
<td>
<b>property</b>: removeUrl
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  removeUrl: 'removeUrl'
<br/>})
</td>
<td>
<b>property</b>: asyncSettings.removeUrl
<br/><br/>
let upload =new Uploader({<br/>
 asyncSettings: {
    removeUrl: 'removeUrl'
  }
<br/>})
</td>
</tr>
<tr>
<td>
Automatically upload the file when files added in to upload queue
</td>
<td>
<b>property:</b> autoUpload
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
   autoUpload: false
<br/>})
</td>
<td>
<b>property:</b> autoUpload<br/><br/>
let upload =new Uploader({<br/>
autoUpload: false
<br/>})
</td>
</tr>
<tr>
<td>
Synchronous upload
</td>
<td>
<b>property:</b>asynUpload
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
     ayncUpload: false
<br/>})

</td>
<td>
No Separate property for enabling synchronous upload.
It can be enabling by using below configuration
<br/><br/>
let upload =new Uploader({<br/>
    autoUpload: false
<br/>})
</td>
</tr>
<tr>
<td>
Key to get the selected files in server side
</td>
<td>
<b>property:</b> uploadName
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
    saveUrl: 'saveUrl',
    uploadName: 'UploadKey'
<br/>})

</td>
<td>
Id of the element used as key value
</td>
</tr>
<tr>
<td>
Upload the files dynamically
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b> upload()
<br/><br/>let uploader =new Uploader({<br/>
asyncSettings: {
   saveUrl: ''
}
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
uploader.upload(filesData)
</td>
</tr>
<tr>
<td>
Event triggers before start to upload the action
</td>
<td>
<b>Event:</b> beforeSend
<br/><br/>
$('#uploader').ejUploadbox({<br/>
   beforeSend: function () {}
<br/>})
</td>
<td>
<b>Event</b>: uploading
<br/><br/>let uploader =new Uploader({<br/>
 uploading: beforeUploadStart
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
function beforeUploadStart() {}
</td>
</tr>
<tr>
<td>
Event triggers when the upload is in progress
</td>
<td>
<b>Event:</b> inProgress
<br/><br/>
$('#uploader').ejUploadbox({<br/>
   inProgress: function () {}
<br/>})
</td>
<td>
<b>Event</b>: progress
<br/><br/>let uploader =new Uploader({<br/>
 progress: uploadingInProgress
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
function uploadingInProgress () {}
</td>
</tr>
<tr>
<td>
Event triggers when upload got success
</td>
<td>
<b>Event:</b>success
<br/><br/>
$('#uploader').ejUploadbox({<br/>
   success: function () {}
<br/>})

</td>
<td>
<b>Event</b>: success
<br/><br/>let uploader =new Uploader({<br/>
 success: uploadingSuccess
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
function uploadingSuccess () {}
</td>
</tr>
<tr>
<td>
Event triggers when upload got failed
</td>
<td>
<b>Event:</b>error
<br/><br/>
$('#uploader').ejUploadbox({<br/>
  error: function () {}
<br/>})

</td>
<td>
<b>Event</b>: failure
<br/><br/>let uploader =new Uploader({<br/>
 failure: uploadingFails
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
function uploadingFails () {}
</td>
</tr>
<tr>
<td>
Event triggers when the upload got started
</td>
<td>
<b>Event:</b>begin
<br/><br/>
$('#uploader').ejUploadbox({<br/>
 begin: function () {}
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Event triggers when cancel the upload
</td>
<td>
<b>Event:</b>cancel
<br/><br/>
$('#uploader').ejUploadbox({<br/>
  cancel : function () {}
<br/>})

</td>
<td>
<b>Event</b>: canceling
<br/><br/>let uploader =new Uploader({<br/>
 canceling: uploadingCancel
<br/>})
<br/>uploader.appendTo('#ej2_Uploader')
function uploadingCancel () {}
</td>
</tr>
<tr>
<td>
Event triggers when the upload completed
</td>
<td>
<b>Event:</b>complete
<br/><br/>
$('#uploader').ejUploadbox({<br/>
  complete : function () {}
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
</table>

## Chunk upload

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Enabling the chunk upload
</td>
<td>
Not Applicable
</td>
<td>
<b>property:</b> asyncSettings.chunkSize<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000
}
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')

</td>
</tr>
<tr>
<td>
Retry the upload automatically when it's get failed
</td>
<td>
Not Applicable
</td>
<td>
<b>property:</b> asyncSettings.retryCount,
         asyncSettings.retryAfterDelay<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000,
   retryCount: 3,
   retryAfterDelay: 1000
}
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')

</td>
</tr>
<tr>
<td>
Pause the uploading file
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b> pause
<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000
   }
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')
<br/>
upload.pause(filesData)
</td>
</tr>
<tr>
<td>
Event triggers when pausing the file
</td>
<td>
Not Applicable
</td>
<td>
<b>Event:</b>pausing<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000
   },<br/>
   pausing: onFilePause
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')
<br/>
function onFilePause() {}
</td>
</tr>
<tr>
<td>
Resuming the paused file
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b> resume
<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000,
   }
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')
<br/>
upload.resume(filesData)
</td>
</tr>
<tr>
<td>
Event triggers when resuming the file
</td>
<td>
Not Applicable
</td>
<td>
<b>Event:</b> resuming <br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000,
   },<br/>
    resuming: onFileResume
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
function onFileResume () {}
</td>
</tr>
<tr>
<td>
Retry the failed file
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b> retry <br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000,
   }
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
upload.retry(filesData)
</td>
</tr>
<tr>
<td>
Cancel the failed file
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b> cancel<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000,
   }
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
upload.cancel(filesData)
</td>
</tr>
<tr>
<td>
Event triggers when cancel the file
</td>
<td>
Not Applicable
</td>
<td>
<b>Event:</b> canceling<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000
   },
   canceling: onFileCancel
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
function onFileCancel(){}
</td>
</tr>
<tr>
<td>
Event triggers when chunk file fails
</td>
<td>
Not Applicable
</td>
<td>
<b>Event:</b>chunkFailure<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000
   },
  chunkFailure: onChunkFail
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
function onChunkFail() {}
</td>
</tr>
<tr>
<td>
Event triggers when chunk file success
</td>
<td>
Not Applicable
</td>
<td>
<b>Event:</b> chunkSuccess<br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   chunkSize: 50000
   },
  chunkSuccess: onChunkSuccess
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
function onChunkSuccess () {}
</td>
</tr>
</table>

## Remove action

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Remove the uploaded file
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b> remove <br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   removeUrl:'removeUrl'
   }
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
upload.remove(filesData)

</td>
</tr>
<tr>
<td>
Event triggers when the file removing succeed
</td>
<td>
<b>Event:</b>remove
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  remove: function() {}
<br/>})
</td>
<td>
<b>Event:</b>success <br/><br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url'
   },<br/>
   Success: onRemoveSuccess
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
function onRemoveSuccess () {}

</td>
</tr>
<tr>
<td>
Event triggers when the file removing fails
</td>
<td>
Not Applicable
</td>
<td>
<b>Event:</b> failure <br/>
let upload =new Uploader({<br/>
  asyncSettings: {
   saveUrl: 'save url',
   removeUrl: 'remove url'
   }, <br/>
   failure: onRemoveFailure
<br/>})<br/>
upload.appendTo('#ej2_uploadBox')<br/>
function onRemoveFailure () {}

</td>
</tr>
</table>

## Buttons

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Customize button text
</td>
<td>
<b>property</b>: buttonText
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  remove: function() {}
<br/>})
</td>
<td>
<b>property</b>: buttons <br/><br/>
 let upload =new Uploader({<br/>
   buttons: {
      browse: 'Choose File',
      clear: 'Clear files',
      upload: 'upload Files'
   }
<br/>})

</td>
</tr>
</table>

## Drag and drop

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
API in Essential JS 1
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Enable drag and drop upload
</td>
<td>
<b>property</b>: allowDragAndDrop
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  allowDragAndDrop: true
<br/>})

</td>
<td>
No separate property to disabling drag and drop
</td>
</tr>
<tr>
<td>
Set custom drop area
</td>
<td>
Not Applicable
</td>
<td>
<b>property</b>:  dropArea <br/><br/>
let upload =new Uploader({<br/>
   dropArea: dropElement
<br/>})

</td>
</tr>
</table>

## Common

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Behavior </b>
</td>
<td>
<b>API in Essential JS 1</b>
</td>
<td>
<b>API in Essential JS 2</b>
</td>
</tr>
<tr>
<td>
Adding custom class to wrapper element
</td>
<td>
<b>property</b>: cssClass
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
     cssClass: 'Custom-Class'
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Enable/Disable the control
</td>
<td>
<b>property</b>: enabled
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
   enabled: false
<br/>})<br/>
<b>Method</b>: enable(), disable()

</td>
<td>
<b>property:</b>enabled <br/><br/>
let upload =new Uploader({<br/>
   enabled: false
<br/>})

</td>
</tr>
<tr>
<td>
Set height for uploader
</td>
<td>
<b>property:</b>height
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  height: '100%'
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Set width for uploader
</td>
<td>
<b>property:</b>width
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
 width: '100%'
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Adding HTML attributes
</td>
<td>
<b>property:</b>htmlAttributes
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
  htmlAttributes: {'aria-label': 'UploadBox'}
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Event triggers when control created successfully
</td>
<td>
<b>Event:</b>create
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
    create: function () {}
<br/>})

</td>
<td>
<b>Event:</b>created
<br/><br/>let uploader =new Uploader({<br/>
 created: function() {}
<br/>})
</td>
</tr>
<tr>
<td>
Event triggers when destroy the control
</td>
<td>
<b>Event:</b>destroy
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
    destroy: function () {}
<br/>})

</td>
<td>
Not Applicable
</td>
</tr>
<tr>
<td>
Keeping the model values in cookies
</td>
<td>
<b>property:</b>enablePersistence
<br/><br/>$('#uploadBox').ejUploadbox({<br/>
    enablePersistence:  true
<br/>})

</td>
<td>
<b>property:</b>enablePersistence
<br/><br/>let uploader =new Uploader({<br/>
 enablePersistence: true
<br/>})
</td>
</tr>
<tr>
<td>
Get the selected files data
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b>getFilesData
<br/><br/>let uploader =new Uploader()<br/>
uploader.appendTo('#uploadbox')<br/>
uploader.getFilesData()
</td>
</tr>
<tr>
<td>
Convert bytes in to MB, GB
</td>
<td>
Not Applicable
</td>
<td>
<b>Method:</b>bytesToSize
<br/><br/>let uploader =new Uploader()<br/>
uploader.appendTo('#uploadbox')<br/>
uploader.bytesToSize(5000)
</td>
</tr>
</table>
