# Register, discover and remove an imperative tool

The supported revision is the [13 November 2026 draft](https://webmachinelearning.github.io/webmcp/). The implementation lives in [registration.mjs](../registration.mjs). It checks all three required methods before using the API, awaits each registration and aborts the shared registration signal if setup fails partway through.

```js
import { createTools } from '../actions.mjs';
import { draftContext, registerTools, invoke } from '../registration.mjs';
const context = draftContext(document);
if (!context) throw new Error('Draft API unavailable in this environment');
const lifecycle = await registerTools(context, [createTools()[0]]);
const result = await invoke(context, 'search_catalog', { query: 'lamp' });
console.log(result.raw); // runtime's serialized response
lifecycle.abort(); // removes the registration
```

invoke discovers the tool object and selects the expected origin before executeTool. It does not pass a bare tool name to the draft execution method. For multi-frame applications, choose the intended window context as well; this demo owns one top-level document and does not test cross-origin delegation.

There are two cancellation lifetimes: registration ends when the page/action context ends; execution ends when a caller aborts one invocation. Keep separate controllers. The demo propagates execution signals into review and cancels pending work on pagehide. Removing registration also cancels the active local action.

Test cleanup through discovery rather than merely checking a local controller's aborted property. Re-register once and check for duplicates. Older navigator.modelContext/unregisterTool examples target another revision and are not a current-draft teardown strategy. Polyfill mode is explicit and versioned; it is not native verification.
