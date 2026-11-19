# WebMCP action examples

Runnable JavaScript examples for a bounded catalogue search, documentation search, fictional service availability and a human-reviewed local support draft. Use these when you need to implement and test a clear tool contract without a framework or unreleased backend. Each example can run independently by selecting its URL parameter. The same handler serves the manual UI and the registered tool.

## Run locally

Requires Node.js 20+; no npm install or runtime network dependencies.

```sh
npm test
npm start
```

Open http://127.0.0.1:4173/?example=catalog. Other examples: ?example=docs, ?example=availability, ?example=request. Source handlers are in [actions.mjs](actions.mjs); registration/caller code in [registration.mjs](registration.mjs); review UX in [review.mjs](review.mjs).

## Compatibility and execution paths

Targets document.modelContext, asynchronous registerTool, getTools, executeTool(RegisteredTool, input) and AbortSignal cleanup from the [13 November 2026 draft](https://webmachinelearning.github.io/webmcp/). This experimental community draft is not a W3C Standard. Chrome documentation/implementations may expose an earlier surface; this project detects the required draft methods and does not silently adapt navigator.modelContext.

The manual control works without WebMCP. The tool control uses actual discovery/execution in the detected draft context. If unavailable, readers may explicitly load the pinned [polyfill 0.1.1](THIRD-PARTY.md). Its mode is visibly labelled, and it does not establish native browser-agent interoperability. HTTPS or a trustworthy localhost origin is required. No external agent integration is claimed from a manual click or a mock test.

## Implementation guides

- [JavaScript handler contracts](docs/webmcp-javascript-example.md)
- [Imperative registration, discovery and teardown](docs/webmcp-imperative-api-example.md)
- [Testing and confirmation workflow](docs/testing-and-confirmation.md)

Declarative forms are not implemented here: the pinned polyfill does not implement them, and a supported declarative browser execution was not verified. Learn that separate surface from [Chrome's guide](https://developer.chrome.com/docs/ai/webmcp).

## Safety and limitations

All data is fictional. A reviewed request is recorded only in page state and is never sent. Human refusal, timeout and abort cannot approve a local draft. Review is a local UX demonstration, not secure server-side authorization. Real mutations require principal/resource checks, payload-bound confirmation, atomic idempotency and recovery on the server. Schema declarations and annotations are hints/contracts; handlers validate input independently.

Node tests cover known outputs, bad types/unknown fields, cancellation, exact review payloads, partial registration rollback and origin selection. Mock lifecycle tests describe intended contracts; browser evidence is recorded separately in [VERIFICATION.md](VERIFICATION.md).

## Related resources and maintenance

[Readiness workflow](https://github.com/raghav453/webmcp-readiness-checklist) · [Security review](https://github.com/raghav453/webmcp-security-checklist) · [Interactive inspector playground](https://github.com/raghav453/webmcp-interactive-playground).

See [MAINTENANCE.md](MAINTENANCE.md), [CONTRIBUTING.md](CONTRIBUTING.md) and [THIRD-PARTY.md](THIRD-PARTY.md). Original code/docs: MIT. Vendored polyfill: Apache-2.0.

Maintained by WebMCPly contributors. [WebMCPly's introduction](https://webmcply.com/what-is-webmcp) provides educational context. WebMCPly's complete platform is in pre-launch: [project information and early access](https://webmcply.com/). This demo is independent of its planned SaaS and does not imply vendor or standards-body endorsement.
