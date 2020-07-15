---
title: "ListBox with icons and customization"
component: "ListBox"
description: "Typescript ListBox supports icons, images and customization of each list elements."
---

# Icons and Customization

## Icons

To place the icon on a list box, set the [`iconCss`](../api/list-box/fieldSettingsModel/#iconcss) property to `e-icons` with the required icon CSS. By default, the icon is positioned to the left side of the list.

In the following sample, icon classes are mapped with `iconCss` field.

{% tab template="list-box/icons", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { ListBox, CheckBoxSelection } from '@syncfusion/ej2-dropdowns';

ListBox.Inject(CheckBoxSelection);

// define the array of object
let data: { [key: string]: Object }[] = [
    { text: 'Settings', iconCss: 'e-list-icons e-list-user-settings' },
    { text: 'Address Book', iconCss: 'e-list-icons e-list-address-book' },
    { text: 'Delete', iconCss: 'e-list-icons e-list-delete' },
    { text: 'Forward', iconCss: 'e-list-icons e-list-forward' },
    { text: 'Reply', iconCss: 'e-list-icons e-list-reply' },
    { text: 'Reply All', iconCss: 'e-list-icons e-list-reply-all' },
    { text: 'Save All Attachments', iconCss: 'e-list-icons e-list-save-all-attachments' },
    { text: 'Save As', iconCss: 'e-list-icons e-list-icon-save-as' },
    { text: 'Touch/Mouse Mode', iconCss: 'e-list-icons e-list-touch' },
    { text: 'Undo', iconCss: ' e-list-icons e-list-undo' }
];

// initialize ListBox component
let listObj: ListBox = new ListBox({
    //set the data to dataSource property
    dataSource: data,
    fields: { text: 'text', iconCss: 'iconCss'}
});
listObj.appendTo('#listbox');

```

{% endtab %}

## Templates

ListBox items can be customized according to the requirement using [`itemTemplate`](../api/list-box/#itemtemplate) property.

In the following sample, the items in the cart are displayed using list box template,

{% tab template="list-box/templates", es5Template="basic", isDefaultActive = "true", sourceFiles="app.ts,index.html,styles.css", iframeHeight="500px" %}

```typescript

import { ListBox  } from '@syncfusion/ej2-dropdowns';

// dataSource definition
let data: { [key: string]: Object; }[] =  [
    { text: 'JavaScript', pic: 'javascript', description: 'It is a lightweight interpreted or JIT-compiled programming language.' },
    { text: 'TypeScript', pic: 'typescript', description: 'It is a typed superset of Javascript that compiles to plain JavaScript.' },
    { text: 'Angular', pic: 'angular', description: 'It is a TypeScript-based open-source web application framework.' },
    { text: 'React', pic: 'react', description: 'A JavaScript library for building user interfaces. It can also render on the server using Node.' },
    { text: 'Vue', pic: 'vue', description: 'A progressive framework for building user interfaces. it is incrementally adoptable.' }
];

// initialize ListBox component
let listBoxObj: ListBox = new ListBox({
    // Set the data source property.
    dataSource: data,
    // set the template content for list items
    itemTemplate:  '<div class="list-wrapper">' +
    '<span class="${pic} e-avatar e-avatar-xlarge e-avatar-circle"></span>' +
    '<span class="text">${text}</span><span class="description">' +
    '${description}</span></div>'
});
listBoxObj.appendTo('#listbox');

```

{% endtab %}

## See Also

* [How to enable or disable items in the list box](./how-to/enable-or-disable-items)