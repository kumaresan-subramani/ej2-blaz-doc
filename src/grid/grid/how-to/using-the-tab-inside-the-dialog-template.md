---
title: "Using the tab inside the dialog template"
component: "Grid"
description: "Learn how to use the tab inside the dialog template."
---

# Using the tab inside the dialog template

You can use the [`tab`](../../../tab/) component inside the dialog edit UI using the dialog template feature. The dialog template feature can be enabled by defining the [`editSettings.mode`](../../api/grid/editSettings/#mode) as `Dialog` and [`editSetting.template`](../../api/grid/editSettings/#template) as SCRIPT element ID or HTML string which holds the template.

To include the tab components in the dialog, follow the given steps:

**Step 1**:

Initialize the template for your tab component.

```html
        <div>
        <div id="edittab"></div>
            <div id="tab1">
                <div class="form-row" >
                    <div class="form-group col-md-6">
                        <div class="e-float-input e-control-wrapper">
                            <input id="OrderID" name="OrderID" type="text" value=${if(isAdd)} '' ${else} ${OrderID} ${/if} ${if(isAdd)} '' ${else} disabled ${/if} />
                            <span class="e-float-line"></span>
                            <label class="e-float-text e-label-top" for="OrderID">Order ID</label>
                        </div>
                    </div>
                </div>
                <div class="form-row" >
                    <div class="form-group col-md-6">
                        <div class="e-float-input e-control-wrapper">
                            <input id="CustomerID" name="CustomerID" type="text" value=${if(isAdd)} '' ${else} ${CustomerID} ${/if} />
                            <span class="e-float-line"></span>
                            <label class="e-float-text e-label-top" for="CustomerID">Customer ID</label>
                        </div>
                    </div>
                </div>
                <button id='next' class='e-info e-btn' style="float: right" type='button'> next</button>
            </div>

            <div id="tab2" style='display: none'>
                <div class="form-row" >
                    <div class="form-group col-md-6">
                        <input type="text" name="ShipCountry" id="ShipCountry" value=${if(isAdd)} '' ${else} ${ShipCountry} ${/if} />
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group col-md-6">
                        <input type="checkbox" name="Verified" id="Verified" ${if(isAdd)} '' ${else} checked ${/if} />
                    </div>
                </div>
                <button id='submit' class='e-info e-btn' style="float: right" type='button'> submit</button>
            </div>
        </div>

```

**Step 2**:

To render the tab component, use the [`actionComplete`](../../api/grid/#actionComplete) event of the grid.

```typescript

    let tabObj: Tab = new Tab({
        showCloseButton: false,
        selecting:  (e) => {if(e.isSwiped) {e.cancel = true;} if(e.selectingIndex === 1) {e.cancel = !validate(1)}},
        items: [
            { header: { 'text': 'Details' }, content: '#tab1' },
            { header: { 'text': 'Verify' }, content: '#tab2' },
        ]
    });
    tabObj.appendTo('#edittab');

```

The following example demonstrates rendering the tab control inside the edit dialog. The tab control contains two tabs. You can fill the first tab and then navigate to the second tab. The validation for first tab will be done before navigating to the second tab.

{% tab template="grid/tabtemplate", sourceFiles="index.ts,index.css,index.html",es5Template="tabtemplate" %}

```typescript
import { Grid, Edit, Toolbar, DialogEditEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { DataUtil } from '@syncfusion/ej2-data';
import { Tab } from '@syncfusion/ej2-navigations';
import { CheckBox } from '@syncfusion/ej2-buttons';

Grid.Inject(Edit, Toolbar);

let countryData: {}[] = DataUtil.distinct(data, 'ShipCountry', true);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog', template: '#dialogtemplate' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true, validationRules: { required: true } },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, validationRules: { required: true } },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265,
    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {

            let tabObj: Tab = new Tab({
                showCloseButton: false,
                selecting:  (e) => {if(e.isSwiped) {e.cancel = true;} if(e.selectingIndex === 1) {e.cancel = !validate(1)}},
                items: [
                    { header: { 'text': 'Details' }, content: '#tab1' },
                    { header: { 'text': 'Verify' }, content: '#tab2' },
                ]
            });
            tabObj.appendTo('#edittab');

            new DropDownList({value: args.rowData.ShipCountry, popupHeight: '200px', floatLabelType: 'Always',
                dataSource: countryData, fields: {text: 'ShipCountry', value: 'ShipCountry'}, placeholder: 'Ship Country'}, args.form.elements.namedItem('ShipCountry') as HTMLInputElement);

            new CheckBox({ label: 'Verified', checked: args.rowData.Verified }, args.form.elements.namedItem('Verified'));
            // Set initail Focus
            if (args.requestType === 'beginEdit') {
                (args.form.elements.namedItem('CustomerID')as HTMLInputElement).focus();
            }

            document.getElementById('next').onclick = () => {
                moveNext();
            }

            function validate(tab) {
                let valid: boolean = true;
                 [].slice.call(document.getElementById('tab' + tab).querySelectorAll('[name]')).forEach(element => {
                    element.form.ej2_instances[0].validate(element.name);
                    if (element.getAttribute('aria-invalid') === 'true'){
                        valid = false;
                    }
                });
                if (!valid) {
                return false;
                }
                return true;
            }

            function moveNext() {
                if (validate(1)) {
                    tabObj.select(1);
                }
            }
            document.getElementById('submit').onclick = () => {
                if (validate(2)) {
                    grid.endEdit();
                }
            }
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}
