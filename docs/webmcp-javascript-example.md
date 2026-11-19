# Build a bounded JavaScript lookup

Use searchCatalog from [actions.mjs](../actions.mjs) when learning handler contracts. It accepts query and an optional finite maxPrice in USD. The original fixture contains a $45 desk lamp, $95 floor lamp and $160 reading chair. A query for lamp with maxPrice 50 must return only lamp-01.

The handler rejects arrays, null, unknown properties, nonstrings, oversized queries and invalid price values before lookup. It returns an explicit projection of public fixture fields plus count and fictionalData. A no-match query returns an empty items array, not a misleading error. The read-only tool uses this function and renders the same result as the manual interface.

```js
import { searchCatalog } from '../actions.mjs';
const result = searchCatalog({ query: 'lamp', maxPrice: 50 });
// result.items[0].id === 'lamp-01'; result.count === 1
```

Documentation search and availability demonstrate two different contracts: a bounded text lookup and a region enum with an explicit unavailable outcome. They reuse validation conventions while keeping task-specific inputs and results. Do not expose a generic “run JavaScript” tool.

Schema describes these limits to callers; direct-handler tests verify enforcement. A real catalogue must authorize protected fields and return authoritative server prices/freshness. Do not transplant fictional data or read-only assumptions into a production purchase tool.

Run npm test, then compare the manual result and the discovered tool's returned string in the [testing workflow](testing-and-confirmation.md).
