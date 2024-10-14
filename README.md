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