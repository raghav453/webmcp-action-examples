# Verify execution and human control

## Reproduce a read-only result

Run npm test and npm start. Open ?example=catalog, record browser/version, origin and visible mode. Run the manual example for lamp with maxPrice 50 and observe lamp-01. If the draft API is absent, explicitly enable the polyfill experiment. Click Discover and invoke tool and record the returned string and displayed execution path. These are two distinct runs.

Remove registration and confirm tool invocation is unavailable. In DevTools, if the recorded runtime supports the draft, await document.modelContext.getTools() and check that search_catalog is absent. Reload to register again. Keep native runs free of the polyfill. A polyfill run demonstrates that experimental library's discovery/execution, not every browser agent.

## Verify the consequential boundary

Open ?example=request. Invoke a fictional message. The dialog displays the exact immutable text and fictional recipient; approve records local state only. Refusal resolves canceled, abort rejects, and timeout after 60 seconds discards review. No network sending is implemented. Test HTML-shaped text and confirm it is displayed as text. Adding confirmed:true must be rejected as an unknown input.

Try invoking another review while one is open: the UI blocks a concurrent run and the reviewer rejects overlapping reviews. Cancel, then invoke a new payload; an earlier decision must not carry over. In a real service, bind confirmation to server-trusted principal, payload and freshness and reauthorize at commit time.

## Record evidence and limitations

Use [VERIFICATION.md](../VERIFICATION.md). Unit tests inspect known fixture data and absence of rendering after abort. Registration/origin tests use contract mocks and do not prove native API behavior. Keep browser discovery/execution and any external-agent test as separate evidence categories. For production, add authorization, atomic replay and fault-recovery integration tests before any pilot.

References: [Chrome setup](https://developer.chrome.com/docs/ai/webmcp), [current draft](https://webmachinelearning.github.io/webmcp/), [companion security matrix](https://github.com/raghav453/webmcp-security-checklist/blob/main/docs/security-test-matrix.md).
