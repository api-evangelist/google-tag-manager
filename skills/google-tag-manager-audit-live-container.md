---
name: Audit what is live in a container and roll back a bad publish
description: Read-only inventory of every container, its version history and the exact configuration serving traffic right now — then republish a known-good version if needed.
api: openapi/google-tag-manager-versions-api-openapi.yml
apis:
  - openapi/google-tag-manager-accounts-api-openapi.yml
  - openapi/google-tag-manager-containers-api-openapi.yml
  - openapi/google-tag-manager-versions-api-openapi.yml
operations: [listAccounts, listContainers, getLiveContainerVersion, listContainerVersionHeaders, getContainerVersion, publishContainerVersion]
generated: '2026-08-13'
method: generated
source: openapi/ (Tag Manager API v2) + https://developers.google.com/tag-platform/tag-manager/api/v2/devguide
---

# Audit the live container

Steps 1–5 are entirely read-only and need only
`https://www.googleapis.com/auth/tagmanager.readonly`. Prefer this scope for any
agent whose job is inventory, governance or reporting — it cannot mutate anything.

## Steps

1. **`listAccounts`** — `GET /tagmanager/v2/accounts`. Paginate on
   `pageToken` / `nextPageToken`.
2. **`listContainers`** — `GET /tagmanager/v2/{parent}/containers` per account path.
   Record `publicId` (`GTM-XXXXXXX`), `name`, `usageContext` and `path`.
3. **`getLiveContainerVersion`** — `GET /tagmanager/v2/{parent}/versions:live`,
   `parent` = container path. This is the **only** authoritative answer to "what is
   running on the site right now." The response embeds the full `tag[]`,
   `trigger[]`, `variable[]` and `builtInVariable[]` set of the live version — one
   call gives you the whole live configuration, so do not walk the workspace
   collections to reconstruct it.
4. **`listContainerVersionHeaders`** — `GET /tagmanager/v2/{parent}/versions`.
   Lightweight headers only (`containerVersionId`, `name`, `numTags`,
   `numTriggers`, `numVariables`, `deleted`). Pass `includeDeleted=true` when you
   need the full history. Paginate with `pageToken`.
5. **`getContainerVersion`** — `GET /tagmanager/v2/{versionPath}` on any header to
   pull that version's full configuration for a diff against live.

## Rollback

6. **`publishContainerVersion`** — `POST /tagmanager/v2/{versionPath}:publish` on the
   last-known-good version from step 4, passing its `fingerprint` as the
   `fingerprint` query parameter. Requires `tagmanager.publish`.
7. Re-run step 3 and confirm `containerVersionId` is the one you intended.

## Rules

- **Live ≠ latest.** The highest `containerVersionId` in step 4 is not necessarily
  live; only step 3 tells you what is serving.
- **Rollback is a forward publish.** There is no undo operation — you republish an
  older immutable version. The version you rolled back *from* stays in history.
- **Step 6 is the escalation boundary.** Everything before it is safe to run
  unattended; step 6 changes live traffic and should require human approval.
- **Budget the audit.** 0.25 QPS per project (25 requests per 100 seconds) means a
  full-estate crawl of many accounts must be paced, not parallelised. Exhaustion
  returns **403** with reason `quotaExceeded` — not 429. Retry with exponential
  backoff `(2^n) + random_ms`, max 5 attempts.
