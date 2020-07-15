---
title: "Localization"
component: "Uploader"
description: "Explains how to localize (locale) all the static text of the file upload control using L10n library that helps to adapt with different cultures."
---

# Localization

The Localization library allows you to localize static text content of the uploader. The static text contains default text content of action buttons, file status, clear icon title, tooltips, and text content of drag area. Define the [locale](../api/uploader/#locale) object for a culture and assign it to L10n load method.

The following are the list of keys and its values used in the uploader component:

| Key | Description |
|------------------------|---------|
| Browse | To customize the browse button text.|
| Clear | To customize the clear button text.|
| Upload | To customize the upload button text. |
| dropFilesHint | To customize the drop area text. |
| uploadFailedMessage | To customize the status text when the file is failed to upload.|
| uploadSuccessMessage | To customize the status text when the file is uploaded successfully.|
| removedSuccessMessage | To customize the status text when the file is removed the successfully from the serve.|
| removedFailedMessage | To customize the status text while the file is failed to remove.|
| inProgress | To customize the status text while the upload is in progress.|
| pauseUpload | To customize the status text while the uploading is paused.|
| fileUploadCancel | To customize the status text when uploading is canceled.|
| readyToUploadMessage | To customize the status text when the file is selected and ready to upload.|
| invalidMaxFileSize | To customize the status text when the file size is greater than the maximum file size.|
| invalidFileType | To customize the status text when the file type is invalid.|
| invalidMinFileSize | To customize the status text when the file size is less than the minimum file size. |
| remove | To customize tooltip text for remove icon. |
| cancel | To customize tooltip text for cancel icon. |
| delete | To customize tooltip text for delete icon. |

{% tab template="uploader/localization", es5Template="locale-template", sourceFiles="app.ts,index.html" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { Uploader } from '@syncfusion/ej2-inputs';
import { detach, L10n } from '@syncfusion/ej2-base';

L10n.load({
    "fr-CH": {
        "uploader": {
            "invalidMinFileSize" : "La taille du fichier est trop petite! S'il vous plaît télécharger des fichiers avec une taille minimale de 10 Ko",
            "invalidMaxFileSize" : "La taille du fichier dépasse 28 Mo",
            "invalidFileType" : "Le type de fichier n'est pas autorisé",
            "Browse"  : "Feuilleter",
            "Clear" : "Clair",
            "Upload" : "Télécharger",
            "dropFilesHint" : "ou Déposer des fichiers ici",
            "uploadFailedMessage" : "Impossible d'importer le fichier",
            "uploadSuccessMessage" : "Fichier téléchargé avec succès",
            "removedSuccessMessage": "Fichier supprimé avec succès",
            "removedFailedMessage": "Le fichier n'a pas pu être supprimé",
            "inProgress": "Téléchargement",
            "readyToUploadMessage": "Prêt à télécharger",
            "remove": "Retirer",
            "cancel": "Annuler",
            "delete": "Supprimer le fichier"
        }
    }
})

    let dropElement: HTMLElement = document.getElementsByClassName('control-fluid')[0] as HTMLElement;
    let uploadObj: Uploader = new Uploader({
        autoUpload: false,
        asyncSettings: {
            saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
            removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
        },
        dropArea: dropElement,
        locale: 'fr-CH'
    });
    uploadObj.appendTo('#fileupload');
```

{% endtab %}
