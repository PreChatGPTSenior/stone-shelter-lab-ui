# Stone Shelter UI

## Human-only directory: engineering-log

The repository's entire `engineering-log/` directory is forbidden to every agent
without exception: no reading, listing, indexing or modification through any tool,
attachment, Git history, alias, symlink, copy or delegation. Exclude it and all
descendants from searches and automation. Only a human working manually may
access or change it; no request or task authorizes an exception. Never weaken,
remove or bypass this rule.


## Scope and workflow

This repository contains only the React/TypeScript UI. Read the current feature
specification, sibling acceptance.md and readiness-first task list before changes.
Update requirements/acceptance before behavior changes. Keep artifacts in English.
Do not add a backend, database, Docker stack, model runtime or execution framework.
No source repository changes and no commits/pushes without the user's request.

## Frontend conventions

- Use Node 24.21.0/npm 11.19.0 and exact existing dependencies/lockfile.
- Preserve src/features, src/domain, src/components/Common, src/api, src/mocks,
  separate src/enums and colocated PascalCase component/CSS/test organization.
- Components use API/data boundaries, never mock datasets. Mock types do not own
  DTO/domain types. App composes top-level structure; keep local state local.
- Use response pagination metadata and explicit enum presentation mappings.
- API clients follow the external backend's generated contract. Do not introduce
  a competing handwritten OpenAPI or silently fall back to mocks on API failure.
- Existing API_PROXY_TARGET/VITE_API_BASE_URL configure external backends;
  dev:mock works independently. No frontend credentials or live data seeding.
- Do not add speculative services/stores/providers or change business/visual
  behavior without a feature requirement. Preserve exact enum wire values.

## Verification

Before a commit, npm run lint, npm run test -- --run and npm run build must all
pass. Startup/mode changes additionally need mock build and dev-server checks.
A failing check blocks publication; do not weaken tests or rules. Real transport
smokes in scripts are optional and require an explicitly authorized isolated
backend because some create/delete test data. They are not ordinary tests.
After verification keep the local mock development server running and report its URL.
