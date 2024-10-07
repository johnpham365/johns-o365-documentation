## Context / Org. Unit Structure
```typescript
import { context } from 'o365-modules';

context.on("Change", function() {
});
```

## Data Objects
```typescript
import { getDataObjectById } from 'o365-dataobject';


dsObject.on("DataLoaded", function(pData) {
});

dsObject.on("AfterSave", function() {
});

function refreshDataObjects() {
    [dsObject].forEach(pDataObject => {
        pDataObject.load();
    });
}
```
