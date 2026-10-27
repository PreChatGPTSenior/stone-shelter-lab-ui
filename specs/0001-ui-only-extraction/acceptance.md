# Acceptance criteria

| ID | Expected result | Verification |
|---|---|---|
| UI-001 | New repository contains frontend source/assets/config/tests and its extraction documentation; no backend, infrastructure, secrets or inherited full Git history | Source/path comparison and final inventory |
| UI-002 | npm ci works on Node 24.21.0/npm 11.19.0; dependency versions remain unchanged | Clean locked install |
| UI-003 | Explicit mock dev and mock build run without any backend; catalog/detail navigation and mock chatbot remain usable | Vite HTTP and real browser smoke |
| UI-004 | API mode retains configurable external backend via API_PROXY_TARGET and optional VITE_API_BASE_URL; /api and /images proxy correctly without silently using mocks | Source review and isolated transport-only proxy probe; no real backend/data/model calls |
| UI-005 | Existing component behavior stays unchanged; lint, full inherited UI unit tests and both API/mock builds pass | Mandatory inherited frontend pre-commit checks and both builds |
| UI-006 | Standalone setup describes both modes, build-time configuration and production SPA/CORS/reverse-proxy responsibility, without requiring backend deployment | Documentation/link review |
| UI-007 | Origin points only to stone-shelter-lab-ui; initial snapshot is published there, source repositories and backup unchanged | Commit/push/ref verification |
