# Standalone Stone Shelter UI extraction

## Goal

Create PreChatGPTSenior/stone-shelter-lab-ui from only stone-shelter-ui in
PreChatGPTSenior/stone-shelter-lab, source main commit
779724164c53f094bf61811ba0f1d40b0cefba49. Source repositories are read-only.
The existing Java backend remains available in its original repository; this
repository supplies the same UI for a later, independently written Python backend.

Keep the existing React/TypeScript UI, routing, assets, mock adapters, DTOs,
HTTP/SSE clients, unit tests, pinned dependencies and Vite configuration. Flatten
its frontend directory into the new repository root. Reuse explicit dev:mock,
dev:api, build:mock and API build modes. Do not change business or visual behavior.

Backend location is configuration, not a new settings screen. Preserve
API_PROXY_TARGET for the development/preview proxy and VITE_API_BASE_URL for an
explicit browser API base selected at build time. Do not embed credentials.
API failures never enable mocks. No backend is needed for mock operation.

## HTTP contract requirements

Preserve every existing UI request route, verb, DTO/enum, status/error handling,
credentials policy and streaming protocol. No server endpoint or handwritten
OpenAPI is added. The external backend's generated contract remains wire authority;
this copy's API clients/types are its consumer implementation. A future Python
backend must expose compatible behavior or explicitly revise the contract first.

## Scope

Copy only the frontend subtree, excluding protected paths, symlinks, deployment
Docker files, secrets, dependencies/caches and build outputs. Retain frontend-only
optional transport smoke helpers but do not run them against a real data service.
Replace monorepo setup/instruction links with concise standalone UI guidance.
No Java, Maven, database, storage, Kafka, Sonar, model runtime or agent coordinator
belongs in the new repository. No source/backup/spec-scaffold modification.

Acceptance is defined exclusively in [acceptance.md](acceptance.md).
