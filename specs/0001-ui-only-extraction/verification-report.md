# UI-only extraction verification — 2026-10-27

Source: PreChatGPTSenior/stone-shelter-lab main
779724164c53f094bf61811ba0f1d40b0cefba49, stone-shelter-ui subtree only.
Destination: PreChatGPTSenior/stone-shelter-lab-ui.

| Check | Observed result |
|---|---|
| Scoped export | 149 regular UI files exported; every original Git blob SHA-1 verified before writing; no full repository or backend history copied |
| Preservation | 147 original files remain byte-identical, including all src/public/API clients, Vite/test/lint configuration, package and lock; README/AGENTS adapted for standalone use |
| Backend exclusion | No Java, pom/Maven wrapper, Compose, Dockerfile, infrastructure, agent runner or backend filesystem dependency |
| Runtime/dependencies | Node 24.21.0/npm 11.19.0; npm ci --ignore-scripts succeeds with unchanged exact lock |
| Lint | npm run lint PASS |
| Inherited unit/component tests | npm run test -- --run PASS: 28 files, 235 tests |
| API build | npm run build PASS; no mock data chunks in the API output |
| Mock build | npm run build:mock PASS; explicit mock chunks emitted; final local dist is mock mode |
| Mock production preview | SPA catalog path and compiled JavaScript return HTTP 200 without backend |
| Configurable external proxy | Actual Vite dev and preview /api and /images routes reach an isolated loopback transport responder; four requests verified; explicit mock mode disables that proxy even when its target is configured |
| Browser | Real in-app browser displays 30 mock stones, Meadow detail/gallery and Mock assistant; a local mock message returns the expected answer and two stone links |
| Source safety | Original local UI is unchanged; remote source is read-only; no source/backup/spec-scaffold writes |

The proxy responder is a temporary transport fixture only, not a Python backend
or evidence of a real backend implementation. No real catalog write, model call,
backend deployment or source-side test was run. Live API smoke helpers remain
optional and were not invoked. The existing unit tests verify API base URL,
DTO/error/stream behavior and absence of API-to-mock fallback.

The local mock development server remains running at
http://127.0.0.1:5173/stone-shelter/catalog. Its process metadata and screenshot
are ignored under .cache/extraction. No environment secrets or generated build
outputs are included in the initial Git snapshot. Publication targets only the
new UI repository with a fresh frontend-only history.
