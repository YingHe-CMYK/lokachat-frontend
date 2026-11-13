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
- End-to-end model latency and native user-folder authorization remain unverified; do not treat this snapshot as a fully validated production service.

No backend credentials, databases, local user files or private backend source are included.
