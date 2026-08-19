---
name: Build a trigger-fired, variable-backed tag and publish it live
description: The marquee Tag Manager flow — create a variable and trigger in a workspace, wire a tag to them, cut a container version, and publish it to the live container.
api: openapi/google-tag-manager-tagmanager-api-openapi.yml
apis:
  - openapi/google-tag-manager-variables-api-openapi.yml
  - openapi/google-tag-manager-triggers-api-openapi.yml
  - openapi/google-tag-manager-tagmanager-api-openapi.yml
  - openapi/google-tag-manager-workspaces-api-openapi.yml
  - openapi/google-tag-manager-versions-api-openapi.yml
operations: [createVariable, createTrigger, createTag, getWorkspaceStatus, createWorkspaceVersion, publishContainerVersion, getLiveContainerVersion]
generated: '2026-08-13'
method: generated
source: openapi/ (Tag Manager API v2) + https://developers.google.com/tag-platform/tag-manager/api/v2/devguide
---

# Build and publish a tag

Prerequisite: you have a workspace `path`
(`accounts/{a}/containers/{c}/workspaces/{w}`) from the provisioning skill.

Scopes: `tagmanager.edit.containers` for steps 1–3,
`tagmanager.edit.containerversions` for step 5, `tagmanager.publish` for step 6.
Publishing needs its own scope — asking for the edit scopes only will fail the last
step 403 `insufficientPermissions` after the work is already done.

## Steps

1. **`createVariable`** — `POST /tagmanager/v2/{parent}/variables`, `parent` = the
   workspace path. Body: `name`, `type`, `parameter[]`. Keep the returned
   `variableId` / `name`; you reference a variable from a tag as `{{Variable Name}}`.
   Skip this step if the value you need is a built-in variable.
2. **`createTrigger`** — `POST /tagmanager/v2/{parent}/triggers`, same `parent`.
   Body: `name`, `type` (e.g. `pageview`, `click`, `customEvent`), and `filter[]` /
   `customEventFilter[]` conditions. Keep the returned `triggerId`.
3. **`createTag`** — `POST /tagmanager/v2/{parent}/tags`, same `parent`. Body:
   `name`, `type`, `parameter[]`, and `firingTriggerId: [<triggerId from step 2>]`.
   A tag with no firing trigger never fires; this is the single most common silent
   failure in this API.
4. **`getWorkspaceStatus`** — `GET /tagmanager/v2/{workspacePath}/status`. Review
   `workspaceChange[]` to confirm exactly what you are about to ship, and check
   `mergeConflict[]` is empty. If it is not, run the sync-and-resolve skill first.
5. **`createWorkspaceVersion`** — `POST /tagmanager/v2/{workspacePath}:create_version`
   with `name` and `notes`. This freezes the workspace into an immutable
   `containerVersion`. Read `containerVersion.path`
   (`accounts/{a}/containers/{c}/versions/{v}`) from the response, and check
   `compilerError` before going further.
6. **`publishContainerVersion`** — `POST /tagmanager/v2/{versionPath}:publish`.
   **This is the live-traffic step.** Pass the version's `fingerprint` as the
   `fingerprint` query parameter so a concurrent publish fails loudly instead of
   overwriting.
7. **`getLiveContainerVersion`** — `GET /tagmanager/v2/{parent}/versions:live`,
   `parent` = the container path. Verify `containerVersionId` matches what you just
   published. Do not treat step 6's 200 as proof; confirm from the live read.

## Rules

- **Order matters.** Variable → trigger → tag → version → publish. A tag created
  before its trigger has nothing to reference.
- **Escalate before step 6.** Steps 1–5 are reversible inside a workspace; step 6
  changes what runs on the customer's site. Treat `publishContainerVersion` as a
  human-approval boundary — this is exactly what
  `agentic-access/google-tag-manager-agentic-access.yml` classifies it as.
- **No idempotency key.** This API has no `Idempotency-Key` header. A retried
  `createTag` creates a *second* tag. On an ambiguous failure, `listTags` and match
  on `name` before retrying — never blind-retry a create.
- **Concurrency is fingerprint-based**, not ETag. Details in
  `conventions/google-tag-manager-conventions.yml`.
- **Rollback** is publishing a previous version: `listContainerVersionHeaders`, pick
  the last-known-good, `publishContainerVersion` on it.
