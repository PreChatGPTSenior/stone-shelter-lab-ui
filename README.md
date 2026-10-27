# Stone Shelter UI

Standalone React + TypeScript UI extracted from
[stone-shelter-lab](https://github.com/PreChatGPTSenior/stone-shelter-lab) at
commit 779724164c53f094bf61811ba0f1d40b0cefba49. No Java backend, database,
storage, model runtime or deployment stack is included. Use it with the existing
Java backend or a future compatible Python backend.

## Install

Use Node 24.21.0 and npm 11.19.0:

```sh
npm ci --ignore-scripts --no-audit --no-fund --cache .cache/npm
```

## Run without a backend

```sh
npm run dev:mock
```

Open the URL printed by Vite and navigate to /stone-shelter/catalog. Existing
catalog, details/gallery, creation, adoption and chat use the explicit mock
boundary. Catalog changes stay in mock memory until reload; chat uses its
existing mock lifecycle. No backend, storage service or model call is required.
API failures never silently select mocks.

## Point the UI at a Java or Python backend

Copy .env.example to .env.local and set the backend origin:

```dotenv
API_PROXY_TARGET=http://127.0.0.1:8000
VITE_API_BASE_URL=
```

Then run:

```sh
npm run dev:api
```

Vite proxies /api and /images to API_PROXY_TARGET in development and preview.
Keep VITE_API_BASE_URL empty for that same-origin proxy. To call a backend directly
from the browser instead, set VITE_API_BASE_URL to its URL; the backend must allow
this UI origin through CORS, including credentials where used. Restart Vite after
changing local environment configuration. Never put credentials in VITE_* settings.

npm run dev and npm run build retain the original API default. The backend may
be written in any language but must implement the existing UI's routes, DTO/enums,
errors, cookie behavior and streaming protocol. Consumer code/types live in
src/api and src/enums. The deployed backend's generated OpenAPI remains contract
authority; this repository does not implement or deploy a backend.

## Build and verify

```sh
npm run lint
npm run test -- --run
npm run build
npm run build:mock
```

The explicit mock build is standalone; the API build uses its configured backend.
The last build determines dist contents. npm run preview previews that artifact;
use npm run preview -- --mode mock after the mock build. VITE_API_BASE_URL is a
build-time value: change it before rebuilding a static artifact. A static host
must serve index.html for SPA routes and either proxy /api and /images or use the
configured direct backend URL. Vite's development proxy is not shipped in dist.

Existing unit/component tests use mocks or controlled fetch stubs and need no
backend. Optional scripts/api-smoke.mjs and scripts/chatbot-smoke.mjs exercise an
external service; do not run them against real/shared data without explicit
approval. No ordinary install/start/test command seeds backend data.

Extraction requirements/evidence: [specs/0001-ui-only-extraction](specs/0001-ui-only-extraction/spec.md).
Source file identities are recorded in source-origin.json. UI src/public content,
frontend tooling configuration and dependency versions are preserved from the
pinned source; only standalone instructions are adapted.
