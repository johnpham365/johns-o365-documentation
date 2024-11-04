## O365 Table Grid
```typescript
import { getDataObjectById } from 'o365-dataobject';

<ODataGrid :dataObject="dsSource" hideActionColumn hideSystemColumn hideMultiselectColumn hideGridMenu>
    <OColumn field="Column_ID" :headerName="$t('Column_ID')" :headerTitle="$t('Column_ID ID')" width="80" :cellrendererparams="`/register/item?ID={{Column_ID}}`" cellrenderer="OLink" sortable/>
    <OColumn field="Column_Created" :headerName="$t('Column_Created')" :headerTitle="$t('Column_Created')" width="100" format="Short Date" disableDistinct sortable readonly/>    
    <OColumn field="Column_Name" :headerName="$t('Column_Name')" :headerTitle="$t('Column_Name')" width="250" sortable/>
    <OColumn field="Column_Number" :headerName="$t('Column_Number')" :headerTitle="$t('Column_Number')" width="100"class="text-end" headerClass="text-end" format="1 234" sortable/>

    <OColumn field="ID" :headerName="$t('DeletedExample')" :headerTitle="$t('DeletedExample')" width="80" v-slot="{ row }" sortable>
        <a :class="{ 'text-decoration-line-through': row.Deleted || row.Closed }">
            {{ row.ID }}
        </a>
    </OColumn>
</ODataGrid>
```

## O365 Properties Grid
```typescript
import { OPropertiesGrid, OPropertiesItem, OPropertiesGroup } from 'o365-data-components';
import { getDataObjectById } from 'o365-dataobject';

    <OPropertiesGrid :dataObject="dsSource">
        <OPropertiesGroup :caption="$t('Details')">
            <OPropertiesItem fieldName="Type" :caption="$t('Type')">
                <input class="w-100 border-0 ps-1" type="text" :title="$t('Type')" v-model="dsSource.current.Type" readonly/>
            </OPropertiesItem>
            <OPropertiesItem fieldName="Title" :caption="$t('Title/Name')">
                <input class="w-100 border-0 ps-1" type="text" :title="$t('Title/Name')"
                    v-model="dsSource.current.Title"/>
            </OPropertiesItem>
            <OPropertiesItem fieldName="OrgUnit_Name" :caption="$t('Org. Unit')">
                <input class="w-100 border-0 ps-1" type="text" :title="$t('Org. Unit')"
                    v-model="dsSource.current.OrgUnit_Name" readonly/>
            </OPropertiesItem>
            <OPropertiesItem fieldName="Created" :caption="$t('Date Created')">
                <ODatePicker
                    class= "w-100 border-0 ps-1"
                    v-model= 'dsSource.current.Created'
                    format= "Short Date"
                    date
                    readonly
                />
            </OPropertiesItem>
            <OPropertiesItem fieldName="Created By" :caption="$t('Created By')">
                <input class="w-100 border-0 ps-1" type="text" :title="$t('Created By')"
                    v-model="dsSource.current.CreatedBy" readonly/>
            </OPropertiesItem>
        </OPropertiesGroup>
    </OPropertiesGrid>
```

## Context / Org. Unit Structure
```typescript
import { context } from 'o365-modules';

// name: string
// id: number
// idPath: string
// orgUnit: string
// isDomain: boolean
// domainId: number | null

context.on("Change", function() {
});
```

## Data Objects
```typescript
import { getDataObjectById } from 'o365-dataobject';

const dsObject = getDataObjectById('dsObject');

dsObject.on("DataLoaded", function(pData) {
});

dsObject.on("AfterSave", function() {
});

function refreshDataObjects() {
    [dsObject].forEach(pDataObject => {
        pDataObject.load();
    });
}

dsObject.recordSource.whereClause = ``;

dsObject.save();
dsObject.cancelChanges();

dsObject.unsetCurrentIndex();
```

## Stored Procedures
```typescript
import { getOrCreateProcedure } from 'o365-modules';

getOrCreateProcedure({
    id: 'procName',
    procedureName: 'astp_Procedure'
}).execute({
    data: data.Value
}).then(() => {
});
```

## Alert / Toast
```typescript
alert('Message', 'success', {autohide: true, delay: 2000, slimVersion: true});
```

## URL Parameters
```typescript
const urlParams = new URLSearchParams(window.location.search);
const ID = computed(() => urlParams.get('ID') ?? 0);
```

## Permissions
```SQL
DISABLE TRIGGER stbl_Database_Permissions_ITrig ON stbl_Database_Permissions;
INSERT INTO stbl_Database_Permissions (Namespace, AllowCreate, AllowAlter, AllowDrop, AllowUsingTables, Person_ID)
VALUES ('%', 1, 1, 1, 1, USER_ID_HERE);
ENABLE TRIGGER stbl_Database_Permissions_ITrig ON stbl_Database_Permissions;
```