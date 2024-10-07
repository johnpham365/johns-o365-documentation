## Context / Org. Unit Structure
```typescript
import { context } from 'o365-modules';

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

## URL Parameters
```typescript
const urlParams = new URLSearchParams(window.location.search);
const ID = computed(() => urlParams.get('ID') ?? 0);
```