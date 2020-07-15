# Overview

The **uploader** component is useful to upload images, documents, and other files to server.
The component is the extended version of HTML5 that is uploaded with multiple file selection, auto upload,
drag and drop, progress bar, preload files, and validation.

## Key features

* **[Asynchronous upload](./async)** - Allows you to upload the files asynchronously.
The upload process requires save and remove action URL to manage upload process in the server.

* **[Drag and drop](./file-source/#drag-and-drop)** - Allows you to drag files from the file explorer and drop into the drop area.
By default, the uploader component act as drop area element.

* **[Directory upload](./file-source/#directory-upload)** - Allows you to upload all files of folders to server.

* **[Paste upload](./file-source/#paste-to-upload)** - Allows you to upload any images which currently copied in the clipboard.

* **[Form supports](./form-support/)** - The selected or dropped files are received as a collection in a
form action when the form is submitted.

* **[Validation](./validation/)** - Validates the selected file size and extension by using the
allowedExtensions, maxFileSize, and minFileSize properties.

* **[Template](./template/)** - You can customize default appearance of the uploader using the template
property along with the buttons property.

* **[Localization](./localization/)** - Supports to localize the text content of action buttons, file status,
clear icon title, tooltips, and text content of drag area.