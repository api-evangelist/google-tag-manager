---
name: Provision a Google Tag Manager container and workspace
description: Find the account, create a container for a site or app, and open a workspace to stage changes in — the entry point for every other Tag Manager API flow.
api: openapi/google-tag-manager-containers-api-openapi.yml
apis:
  - openapi/google-tag-manager-accounts-api-openapi.yml
  - openapi/google-tag-manager-containers-api-openapi.yml
  - openapi/google-tag-manager-workspaces-api-openapi.yml
operations: [listAccounts, createContainer, listContainers, createWorkspace, listWorkspaces]
generated: '2026-08-13'
method: generated
source: openapi/ (Tag Manager API v2) + https://developers.google.com/tag-platform/tag-manager/api/v2/devguide
---

# Provision a container and workspace

Base URL `https://tagmanager.googleapis.com`, all paths prefixed `/tagmanager/v2`.
Auth is OAuth 2.0 authorization code only — there are no API keys. Send
`Authorization: Bearer <token>`.

## Before you start

- Enable the Tag Manager API on the calling Google Cloud project, or the first call
  fails 403 `accessNotConfigured`.
- Consent to `https://www.googleapis.com/auth/tagmanager.manage.accounts` (to read
  accounts) and `.../tagmanager.edit.containers` (to create the container and
  workspace). Full scope list: `scopes/google-tag-manager-scopes.yml`.
- **There is no sandbox.** Every call hits production, and the developer guide is
  explicit that destructive operations have "no warnings, no confirmations, and no
  undo." Use a dedicated test account. See `sandbox/google-tag-manager-sandbox.yml`.

## Steps

1. **`listAccounts`** — `GET /tagmanager/v2/accounts`. Returns `account[]`; take the
   `path` of the target account (form `accounts/{account_id}`). Paginate with
   `pageToken` while `nextPageToken` is present.
2. **`listContainers`** — `GET /tagmanager/v2/{parent}/containers` with `parent` set
   to the account `path`. Check whether the container already exists before creating
   a duplicate; match on `name` or `publicId` (the `GTM-XXXXXXX` id).
3. **`createContainer`** — `POST /tagmanager/v2/{parent}/containers`, same `parent`.
   Body needs `name` and `usageContext` (e.g. `["web"]`, `["android"]`, `["ios"]`,
   `["server"]`). The response carries the container `path`
   (`accounts/{a}/containers/{c}`) and the `publicId` you put in the page snippet.
4. **`listWorkspaces`** — `GET /tagmanager/v2/{parent}/workspaces` with `parent` set
   to the container `path`. A new container already has a `Default Workspace`.
5. **`createWorkspace`** — `POST /tagmanager/v2/{parent}/workspaces` with a `name`
   (and optional `description`) when you want an isolated workspace for this change.
   Keep the returned workspace `path`
   (`accounts/{a}/containers/{c}/workspaces/{w}`) — every tag, trigger and variable
   operation hangs off it.

## Rules

- **Resource paths, not ids.** Every operation after `listAccounts` addresses
  resources by the composite `path` string returned by the previous call. Build
  paths from responses; do not concatenate ids by hand.
- **Workspace = isolation.** Nothing you do inside a workspace affects the live
  container until you version and publish it. That is the closest thing this API has
  to a staging environment.
- **Quota is per project, not per user.** 10,000 requests/day and 0.25 QPS
  (25 per 100s) shared across every user of your integration. Cache the account and
  container lookups; do not re-list on every operation.
- **Errors**: branch on `error.errors[0].reason`, never on the message text. Retry
  only `userRateLimitExceeded` and `quotaExceeded`, with exponential backoff
  `(2^n) + random_ms`, max 5 attempts. Note that throttling here is **403, not 429**.
  See `errors/google-tag-manager-problem-types.yml`.
