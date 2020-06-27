---
title: "Scrolling"
component: "DocumentEditor"
description: "Learn scrolling and zooming can be customized in JavaScript document editor."
---

# Scrolling

The Document editor renders the document as page by page. You can scroll through the pages by mouse wheel or touch interactions. You can also scroll through the page by using ‘scrollToPage()’ method of document editor instance. Refer to the following code example.

{% tab template="document-editor/scrolling-zooming", es5Template="scrolltopage", sourceFiles="index.ts,index.html" %}

```typescript

import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.appendTo('#DocumentEditor');
onLoadDefault();
documenteditor.scrollToPage(2);

 function onLoadDefault(): void {
    let defaultDocument: object = {
    "sections": [
        {
            "blocks": [
                {
                    "paragraphFormat": {
                        "styleName": "Normal"
                    },
                    "inlines": [
                        {
                            "text": "First page"
                        }
                    ]
                }
            ],
            "headersFooters": {},
        },
        {
            "blocks": [
                {
                    "paragraphFormat": {
                        "styleName": "Normal"
                    },
                    "inlines": [
                        {
                            "text": "Second page"
                        }
                    ]
                }
            ],
            "headersFooters": {},
        }
    ],
    "characterFormat": {},
    "paragraphFormat": {},
    "background": {
        "color": "#FFFFFFFF"
    },
    "styles": [
        {
            "type": "Paragraph",
            "name": "Normal",
            "next": "Normal"
        },
        {
            "type": "Character",
            "name": "Default Paragraph Font"
        }
    ]
}
documenteditor.open(JSON.stringify(defaultDocument));
documenteditor.focusIn();
}

```

{% endtab %}

> Calling this method brings the specified page into view but doesn’t move selection. Hence this method will work by default. That is, it works even if selection is not enabled.

In case, if you wish to move the selection to any page in document editor and bring it into view, you can use ‘goToPage()’ method of selection instance. Refer to the following code example.

{% tab template="document-editor/scrolling-zooming", es5Template="scroll", sourceFiles="index.ts,index.html" %}

```typescript

import { DocumentEditor} from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.enableAllModules();
documenteditor.appendTo('#DocumentEditor');
onLoadDefaultDocument();
documenteditor.viewer.selection.goToPage(3);

 function onLoadDefaultDocument(): void {
    let defaultDocument: object = {
    "sections": [
        {
            "blocks": [
                {
                    "paragraphFormat": {
                        "styleName": "Normal"
                    },
                    "inlines": [
                        {
                            "text": "First page"
                        }
                    ]
                }
            ],
            "headersFooters": {},
        },
        {
            "blocks": [
                {
                    "paragraphFormat": {
                        "styleName": "Normal"
                    },
                    "inlines": [
                        {
                            "text": "Second page"
                        }
                    ]
                }
            ],
            "headersFooters": {},
        },
        {
            "blocks": [
                {
                    "paragraphFormat": {
                        "styleName": "Normal"
                    },
                    "inlines": [
                        {
                            "text": "Third page"
                        }
                    ]
                }
            ],
            "headersFooters": {},
        }
    ],
    "characterFormat": {},
    "paragraphFormat": {},
    "background": {
        "color": "#FFFFFFFF"
    },
    "styles": [
        {
            "type": "Paragraph",
            "name": "Normal",
            "next": "Normal"
        },
        {
            "type": "Character",
            "name": "Default Paragraph Font"
        }
    ]
}
documenteditor.open(JSON.stringify(defaultDocument));
documenteditor.focusIn();
}
```

{% endtab %}

## Zooming

You can scale the contents in document editor ranging from 10% to 500% of the actual size. You can achieve this using mouse or touch interactions. You can also use ‘zoomFactor’ property of document editor instance. The value can be specified in a range from 0.1 to 5. Refer to the following code example.

```typescript

import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.enableAllModules();
documenteditor.appendTo('#DocumentEditor');
documenteditor.zoomFactor = 3;
```

## Page Fit Type

Apart from specifying the zoom factor as value, the Document editor provides option to specify page fit options such as fit to full page or fit to page width. You can set this option using ‘fitPage’ method of document editor instance. Refer to the following code example.

```typescript

import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.enableAllModules();
documenteditor.appendTo('#DocumentEditor');
documenteditor.fitPage('Fit page width');

```

## Zoom option using UI

The following code example shows how to provide zoom options in document editor.
{% tab template="document-editor/scrolling-zooming", es5Template="base", sourceFiles="index.ts,index.html" %}

```typescript

import { DocumentEditor } from '@syncfusion/ej2-documenteditor';
import { createElement } from '@syncfusion/ej2-base';
import { DropDownButton, ItemModel, MenuEventArgs } from '@syncfusion/ej2-splitbuttons';

let documenteditor: DocumentEditor = new DocumentEditor({
    isReadOnly: false
});
documenteditor.enableAllModules();
documenteditor.appendTo('#DocumentEditor');
let statusBarDiv = document.getElementById('page-fit-type-div');
let startPage: number = 1;
let label: HTMLElement = createElement('label', { styles: 'margin-top: 6px;margin-right: 2px' });
label.textContent = 'Page ';
statusBarDiv.appendChild(label);
let pageNumberLabel = createElement('label', { id: 'documenteditor_page_no', styles: 'text-transform:capitalize;white-space:pre;overflow:hidden;user-select:none;cursor:text;height:17px;max-width:150px' });
let editablePageNumber = createElement('div', { id: 'editablePageNumber', styles: 'border: 1px solid #F1F1F1;display: inline-flex;height: 17px;padding: 0px 4px;', className: 'single-line e-de-pagenumber-text' });
editablePageNumber.appendChild(pageNumberLabel);
updatePageNumber();
statusBarDiv.appendChild(editablePageNumber);
editablePageNumber.setAttribute('title', 'The current page number in the document. Click or tap to navigate specific page.');
let label1: HTMLElement = createElement('label', { id: 'documenteditor_pagecount', styles: 'margin-left:2px;letter-spacing: 1.05px;' });
label1.textContent = 'of';
statusBarDiv.appendChild(label1);
let pageCount = createElement('label', { id: 'documenteditor_pagecount', styles: 'margin-left:6px;letter-spacing: 1.05px;' });
updatePageCount();
statusBarDiv.appendChild(pageCount);
let editorPageCount = undefined;
let zoom: DropDownButton;
let zoomBtn: HTMLButtonElement = createElement('button', {
    id: 'documenteditor-zoom',
    // tslint:disable-next-line:max-line-length
    className: 'e-de-statusbar-zoom'
}) as HTMLButtonElement;
statusBarDiv.appendChild(zoomBtn);
zoomBtn.setAttribute('title', 'Zoom level. Click or tap to open the Zoom options.');
let items: ItemModel[] = [
    {
        text: '200%',
    },
    {
        text: '175%',
    },
    {
        text: '150%',
    },
    {
        text: '125%',
    },
    {
        text: '100%',
    },
    {
        text: '75%',
    },
    {
        text: '50%',
    },
    {
        text: '25%',
    },
    {
        separator: true
    },
    {
        text: 'Fit one page'
    },
    {
        text: 'Fit page width',
    },
];
zoom = new DropDownButton({ content: '100%', items: items, select: onZoom }, zoomBtn);
editablePageNumber.addEventListener('click', updateDocumentEditorPageNumber);
editablePageNumber.addEventListener('keydown', onKeyDown);
editablePageNumber.addEventListener('blur', onBlur);
documenteditor.viewChange = (e): void => {
    updatePageNumberOnViewChange(e);
};
documenteditor.contentChange = (): void => {
    //Set page count
    updatePageCount();
};
function updatePageNumberOnViewChange(args) {
    if (documenteditor.selection
        && documenteditor.selection.startPage >= args.startPage && documenteditor.selection.startPage <= args.endPage) {
        startPage = documenteditor.selection.startPage;
    } else {
        startPage = args.startPage;
    }
    updatePageNumber();
}
function onBlur() {
    if (editablePageNumber.textContent === '' || parseInt(editablePageNumber.textContent, 0) > editorPageCount) {
        updatePageNumber();
    }
    editablePageNumber.contentEditable = 'false';
}
function onKeyDown(e) {
    if (e.which === 13) {
        e.preventDefault();
        let pageNumber: number = parseInt(editablePageNumber.textContent, 0);
        if (pageNumber > editorPageCount) {
            updatePageNumber();
        } else {
            if (documenteditor.selection) {
                documenteditor.selection.goToPage(parseInt(editablePageNumber.textContent, 0));
            } else {
                documenteditor.scrollToPage(parseInt(editablePageNumber.textContent, 0));
            }
        }
        editablePageNumber.contentEditable = 'false';
        if (editablePageNumber.textContent === '') {
            updatePageNumber();
        }
    }
    if (e.which > 64) {
        e.preventDefault();
    }
}
function onZoom(args) {
    setZoomValue(args.item.text);
    updateZoomContent();
}
function setZoomValue(text) {
    if (text.match('Fit one page')) {
        documenteditor.fitPage('FitOnePage');
    } else if (text.match('Fit page width')) {
        documenteditor.fitPage('FitPageWidth');
    } else {
        documenteditor.zoomFactor = parseInt(text, 0) / 100;
    }
}
function updateZoomContent() {
    zoom.content = Math.round(documenteditor.zoomFactor * 100) + '%';
}
function updatePageNumber() {
    pageNumberLabel.textContent = startPage.toString();
}
function updatePageCount() {
    editorPageCount = documenteditor.pageCount;
    pageCount.textContent = editorPageCount.toString();
}
function updateDocumentEditorPageNumber() {
    let editablePageNumber = document.getElementById('editablePageNumber');
    editablePageNumber.contentEditable = 'true';
    editablePageNumber.focus();
    window.getSelection().selectAllChildren(editablePageNumber);
}
```

{% endtab %}
