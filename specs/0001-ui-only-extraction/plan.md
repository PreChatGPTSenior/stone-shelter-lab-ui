# Extraction plan

Use the current requested GitHub source commit rather than the older local HEAD.
Read/export only the frontend subtree. Inventory names before metadata; exclude
engineering-log before traversal, reject symlinks and never fetch the full repository.
Copy regular frontend blobs byte-for-byte into the destination root. Preserve
all src/public/test/client/config content. Exclude only Dockerfile/.dockerignore;
rewrite README/AGENTS for standalone paths, create a gitignore and source record.

Do not add frameworks, modify UI features, write Python/Java backend code or
implement a runtime backend picker. Existing environment variables and Vite modes
already satisfy the requested connection configuration. Keep existing frontend
scripts/tests and exact dependency lock; only package name may be adjusted with
its root lock metadata if useful.

T0001-001 first checks the whole T0001-001/T0001-002 batch: source commit/UI access,
destination ownership, Node/npm versions, GitHub create/write capability and
available verification resources. Mock/frontend operation requires no JDK, Docker,
backend, storage, Kafka or model. Report stopped source application services with
no impact and do not start them.

T0001-002 copies only the UI and creates standalone docs, installs exact locked
dependencies, then runs npm run lint, npm run test -- --run, npm run build and
npm run build:mock. These inherited full UI checks are explicitly the selected
validation level for extraction/publication; no backend suite or live smoke runs.
Use a temporary local HTTP responder only for proxy plumbing, not as a Python
backend or evidence of a real implementation. Use the installed browser/runtime
for a real mock-mode catalog/detail/chat navigation check. Leave the mock dev
server running and report its URL. Publish the initial UI-only snapshot to the
explicitly requested new GitHub repository after verification; never push to the source.

Writable scope: destination frontend src/**, public/**, scripts/** and root
frontend package/lock/config/env-example files copied from the pinned source;
standalone README.md, AGENTS.md, .gitignore, source-origin.json and this feature's
spec/acceptance/plan/tasks/readiness/verification documents. No sibling writes.
