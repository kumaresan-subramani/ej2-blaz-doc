---
title: "Server-side export"
component: "DocumentEditor"
description: "Learn how to perform export of SFDT to other MS Word formats and PDF document in server-side."
---

# Server-side export

## Sfdt to Docx export

Document editor supports server-side export of **Syncfusion Document Text (.sfdt)** to Doc, Docx, Rtf, Txt, WordML, Html formats using server-side helper **Syncfusion.EJ2.DocumentEditor** available in ASP.NET Core & ASP.NET MVC platform in the below nugets.

* [Syncfusion.EJ2.WordEditor.AspNet.Core](https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Core)
* [Syncfusion.EJ2.WordEditor.AspNet.Mvc5](https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Mvc5)
* [Syncfusion.EJ2.WordEditor.AspNet.Mvc4](https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Mvc4)

Please refer the following code example.

```csharp

//API controller for the conversion.
[HttpPost]
public void ExportSFDT([FromBody]SaveParameter data)
{
    Stream document = WordDocument.Save(data.content, FormatType.Docx);
    FileStream file = new FileStream("sample.docx", FileMode.OpenOrCreate, FileAccess.ReadWrite);
    document.CopyTo(file);
    file.Close();
    document.Close();
}

public class SaveParameter
{
    public string content { get; set; }
}

```

Please refer the client side example to serialize the sfdt and send to the server.

```typescript
import { DocumentEditor, FormatType, WordExport, SfdtExport } from '@syncfusion/ej2-documenteditor';

DocumentEditor.Inject(WordExport, SfdtExport);

let documenteditor: DocumentEditor = new DocumentEditor({ enableSfdtExport: true, enableWordExport: true, enableTextExport: true });

documenteditor.appendTo('#DocumentEditor');

documenteditor.open(sfdt);

document.getElementById('export').addEventListener('click', () => {
    let http: XMLHttpRequest = new XMLHttpRequest();
    http.open('POST', 'http://localhost:5000/api/documenteditor/ExportSFDT');
    http.setRequestHeader('Content-Type', 'application/json;charset=UTF-8');
    http.responseType = 'json';
    let sfdt: any = { content: documenteditor.serialize() };
    http.send(JSON.stringify(sfdt));
});

```

> DocumentEditor object is available in DocumentEditorContainer component(DocumentEditor packaged with toolbar, statusbar & properties pane) as [`documentEditor`](../api/document-editor-container#documenteditor-code-classlanguage-textdocumenteditorcode/)
