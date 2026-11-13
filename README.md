# LokaChat frontend

Current frontend source snapshot (2026-11-13).

Live experience: https://loka-chat-mirror-v1.yinghe-vela-live.workers.dev/design

## Run locally

Node.js 24 or newer.

```sh
npm ci
npm run dev
```

Run `npm run build` for a production bundle. `/api` requests are proxied to localhost:8780 during development; the account, points and connector backend is not included in this frontend repository.

## Entry points

- `/design.html`: public introduction
- `/experience/index.html#17`: local source permission
- `/experience/index.html#19`: Mirror
- `/?identity=1`: account authentication UI

## Status

- White responsive frontend, native folder preview, purpose selection, swipe correction and local inference client included.
- Email registration requires configured authentication backend. No real account is fabricated.
- Loka Points (LP) balance and activity require authenticated server endpoints; no purchase, transfer or cash redemption is enabled.
- Local inference requires a downloaded model and Ollama on the same device. No cloud fallback. Physical-phone local inference is not delivered.
- Real local-model interaction is tested on a controlled corpus in mobile/desktop browser viewports. Native user-folder authorization and physical-phone local inference remain unverified; this is not a fully validated production service.

No backend credentials, databases, local user files or private backend source are included.

## Mirror interaction update

Active interview, pointer left-swipe correction and local plan recomputation share a cancellable, versioned request lifecycle. Old requests cannot overwrite revised plans. Model response failures show retry rather than a scripted answer. Identical corrections are not re-recorded. Draft input survives rerenders. Previous and revised plans are visible together. After reload, reconnect sources to recompute; the saved plan is retained read-only. No points are awarded or deducted by swipes, model responses or retries.

Recommended local model for verification: `ollama pull qwen2.5:7b`. Model selection stays visible and configurable. Never treat a generated plan or a successful integration test as a verified prediction.

### Reproduce interaction checks

`npm test` checks request supersession, cancellation and retry. For browser checks, install Playwright separately (`npm install --no-save playwright` and `npx playwright install chromium`), serve this frontend, and run `BASE=http://127.0.0.1:5173/experience MODEL=qwen2.5:7b npm run test:mirror`. Set `WIDTH=1440` for desktop and `CHECK=1` to include the alternatives/check flow.

The browser test uses a controlled file-picker adapter and a labeled QA corpus; it is not a real OS folder-picker or physical-phone test. Inference itself uses the actual downloaded local model. The test compares before/after plans, verifies source withdrawal and model-unavailable behavior, and rejects record-bearing requests outside loopback. Production model accuracy and physical-phone runtime are separate validation tasks.

### Verified correction case (2026-11-13)

Controlled QA record: the end date was not agreed, weekday availability and a 400-dollar budget. Before correction, the plan was to finalize the end date. The person then confirmed the date was settled and changed availability to Tuesdays only. The recomputed plan switched to preparing a Tuesday-only task schedule within the same budget. Both plans remain in history. This tests integration behavior on one corpus, not prediction accuracy.

Browser checks include native-picker cancellation through a controlled adapter, preview and separate use/training selection, real local-model questions, actual pointer left-swipe, correction submission and return editing, plan comparison, editable draft, reload/reconnect, withdrawal, model-unavailable errors and absence of record-bearing cloud requests.
