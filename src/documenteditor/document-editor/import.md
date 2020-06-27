---
title: "Import"
component: "DocumentEditor"
description: "Learn how to import SFDT and word documents in JavaScript document editor using supported APIs."
---

# Import

In Document Editor, the documents are stored in its own format called **Syncfusion Document Text (SFDT)**.

The following example shows how to open SFDT data in Document Editor.

{% tab template="document-editor/import", es5Template="sfdt-import", sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor();

documenteditor.appendTo('#DocumentEditor');

let sfdt: string =`{
    "sections": [
        {
            "blocks": [
                {
                    "inlines": [
                        {
                            "characterFormat": {
                                "bold": true,
                                "italic": true
                            },
                            "text": "Hello World"
                        }
                    ]
                }
            ],
            "headersFooters": {
            }
        }
    ]
}`;

documenteditor.open(sfdt);
```

{% endtab %}

## Import document from local machine

The following example shows how to import document from local machine.

{% tab template="document-editor/import-sfdt", es5Template="import", sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor();

documenteditor.appendTo('#DocumentEditor');

document.getElementById('file_upload').setAttribute('accept', '.sfdt');

document.getElementById("import").addEventListener("click", (): void => {
    document.getElementById('file_upload').click();
});

document.getElementById('file_upload').addEventListener("change", (e: any): void => {
    if (e.target.files[0]) {
        let file = e.target.files[0];
        if (file.name.substr(file.name.lastIndexOf('.')) === '.sfdt') {
            let fileReader: FileReader = new FileReader();
            fileReader.onload = (e: any) => {
                let contents: string = e.target.result;
                documenteditor.open(contents);
            };
            fileReader.readAsText(file);
            documenteditor.documentName = file.name.substr(0, file.name.lastIndexOf('.'));
        }
    }
});

```

{% endtab %}

## Convert word documents into SFDT

You can convert word documents into SFDT format using the .NET Standard library [`Syncfusion.EJ2.WordEditor.AspNet.Core`](<https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Core/>) by the web API service implementation. This library helps you to convert word documents (.dotx,.docx,.docm,.dot,.doc), rich text format documents (.rtf), and text documents (.txt) into SFDT format. Refer to the following example.

```typescript
import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor();

documenteditor.appendTo('#DocumentEditor');

document.getElementById('file_upload').setAttribute('accept', '.dotx,.docx,.docm,.dot,.doc,.rtf,.txt,.xml,.sfdt');

document.getElementById("import").addEventListener("click", (): void => {
    document.getElementById('file_upload').click();
});

document.getElementById('file_upload').addEventListener("change", (e: any): void => {
    if (e.target.files[0]) {
        let file = e.target.files[0];
        if (file.name.substr(file.name.lastIndexOf('.')) !== '.sfdt') {
            loadFile(file);
        }
    }
});

function loadFile(file: File): void {
    let ajax: XMLHttpRequest = new XMLHttpRequest();
    ajax.open('POST', 'https://localhost:4000/api/documenteditor/Import', true);
    ajax.onreadystatechange = () => {
        if (ajax.readyState === 4) {
            if (ajax.status === 200 || ajax.status === 304) {
                // open SFDT text in document editor
                documenteditor.open(ajax.responseText);
            }
        }
    }
    let formData: FormData = new FormData();
    formData.append('files', file);
    ajax.send(formData);
}
```

Here’s how to handle the server-side action for converting word document in to SFDT.

```csharp
[AcceptVerbs("Post")]
public string Import(IFormCollection data)
{
    if (data.Files.Count == 0)
        return null;
    Stream stream = new MemoryStream();
    IFormFile file = data.Files[0];
    int index = file.FileName.LastIndexOf('.');
    string type = index > -1 && index < file.FileName.Length - 1 ?
        file.FileName.Substring(index) : ".docx";
    file.CopyTo(stream);
    stream.Position = 0;

    WordDocument document = WordDocument.Load(stream, GetFormatType(type.ToLower()));
    string sfdt = Newtonsoft.Json.JsonConvert.SerializeObject(document);
    document.Dispose();
    return sdft;
}

internal static FormatType GetFormatType(string format)
{
    if (string.IsNullOrEmpty(format))
        throw new NotSupportedException("EJ2 DocumentEditor does not support this file format.");
    switch (format.ToLower()) {
        case ".dotx":
        case ".docx":
        case ".docm":
        case ".dotm":
            return FormatType.Docx;
        case ".dot":
        case ".doc":
            return FormatType.Doc;
        case ".rtf":
            return FormatType.Rtf;
        case ".txt":
            return FormatType.Txt;
        case ".xml":
            return FormatType.WordML;
        default:
            throw new NotSupportedException("EJ2 DocumentEditor does not support this file format.");
    }
}

```

## See Also

* [Feature modules](../document-editor/feature-module/)