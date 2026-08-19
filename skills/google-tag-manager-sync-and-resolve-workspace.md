---
name: Sync a stale workspace and resolve merge conflicts before versioning
description: Bring a workspace up to date with the latest published container version, detect merge conflicts, and resolve them so a version can be cut cleanly.
api: openapi/google-tag-manager-workspaces-api-openapi.yml
apis:
  - openapi/google-tag-manager-workspaces-api-openapi.yml
  - openapi/google-tag-manager-tagmanager-api-openapi.yml
  - openapi/google-tag-manager-versions-api-openapi.yml
operations: [listWorkspaces, getWorkspace, syncWorkspace, getWorkspaceStatus, updateTag, createWorkspaceVersion]
generated: '2026-08-13'
method: generated
source: openapi/ (Tag Manager API v2) + https://developers.google.com/tag-platform/tag-manager/api/v2/devguide
---

# Sync and resolve a workspace

A workspace is a branch off the published container version. When someone else
publishes while your workspace is open, your workspace goes stale and
`createWorkspaceVersion` will either fail or ship a stale configuration. Sync first.

## Steps

1. **`listWorkspaces`** — `GET /tagmanager/v2/{parent}/workspaces`, `parent` = the
   container path. Pick the target workspace `path`.
2. **`getWorkspaceStatus`** — `GET /tagmanager/v2/{workspacePath}/status`. Read:
   - `workspaceChange[]` — every entity changed in this workspace and its
     `changeStatus` (added / updated / deleted).
   - `mergeConflict[]` — entities that changed both in the workspace *and* in the
     base version since the workspace was created.
   If `mergeConflict[]` is empty and `workspaceChange[]` is what you expect, skip to
   `createWorkspaceVersion`.
3. **`syncWorkspace`** — `POST /tagmanager/v2/{workspacePath}:sync`. Rebases the
   workspace onto the latest container version. The response returns
   `syncStatus` (`mergeConflict`, `syncError`) and a `mergeConflict[]` array where
   each entry carries `entityInWorkspace` and `entityInBaseVersion`.
4. **Resolve each conflict.** For every `mergeConflict[]` entry, decide which side
   wins and write the resolved entity back with the matching update operation —
   `updateTag` on `{tagPath}`, `updateTrigger` on `{triggerPath}`, `updateVariable`
   on `{variablePath}` — passing the **`fingerprint` from `entityInWorkspace`** as
   the `fingerprint` query parameter. Resolving means writing the merged entity; the
   API does not pick a winner for you.
5. **`getWorkspaceStatus`** again — confirm `mergeConflict[]` is now empty.
6. **`createWorkspaceVersion`** — `POST /tagmanager/v2/{workspacePath}:create_version`
   with `name` and `notes`. Check `compilerError` on the response before publishing.

## Rules

- **Always sync before versioning** in any multi-user container. A version cut from a
  stale workspace silently reverts whatever the other publisher shipped.
- **`syncWorkspace` is not idempotent in effect.** It rebases; re-running after you
  have started resolving conflicts can reintroduce them. Sync once, then resolve.
- **A conflict is a human decision.** An agent may detect and report
  `mergeConflict[]`, but choosing `entityInWorkspace` over `entityInBaseVersion`
  discards someone else's published work — escalate rather than auto-resolve.
- **`getWorkspaceStatus` is the pre-flight check** for the publish flow. Run it as
  step 4 of the build-and-publish skill too.
- Quota: 0.25 QPS per project. Conflict-resolution loops over many entities will hit
  it — pace the writes and back off on `403` / `userRateLimitExceeded`.
