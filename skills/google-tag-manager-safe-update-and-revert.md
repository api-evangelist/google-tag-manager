---
name: Safely update or revert a tag, trigger or variable
description: Read-modify-write against Tag Manager's fingerprint-based optimistic concurrency, and undo an unpublished workspace change with the :revert operations.
api: openapi/google-tag-manager-tagmanager-api-openapi.yml
apis:
  - openapi/google-tag-manager-tagmanager-api-openapi.yml
  - openapi/google-tag-manager-triggers-api-openapi.yml
  - openapi/google-tag-manager-variables-api-openapi.yml
operations: [getTag, updateTag, revertTag, getTrigger, updateTrigger, revertTrigger, getVariable, updateVariable, revertVariable]
generated: '2026-08-13'
method: generated
source: openapi/ (Tag Manager API v2) + https://developers.google.com/tag-platform/tag-manager/api/v2/devguide
---

# Safe update and revert

Tag Manager has no ETag / `If-Match` header. It uses a **`fingerprint`** field on
every resource, changed on every modification, passed back as a **query parameter**
on update. This is the concurrency contract for the whole API.

## Update (read-modify-write)

1. **`getTag`** — `GET /tagmanager/v2/{tagPath}` (or `getTrigger` on `{triggerPath}`,
   `getVariable` on `{variablePath}`). Keep the whole entity **and** its
   `fingerprint`.
2. Apply your changes to the entity you just read. `updateTag` is `PUT` — a full
   replace, not a patch. Fields you omit are dropped. Never construct the body from
   scratch; always mutate the object from step 1.
3. **`updateTag`** — `PUT /tagmanager/v2/{tagPath}?fingerprint=<from step 1>` with the
   modified entity as the body.
   - `200` — applied. The response carries a **new** `fingerprint`; use that one for
     any subsequent write.
   - `409` — someone else changed the resource since your read. Go back to step 1,
     re-apply, retry. Do **not** re-send without re-fetching, and do **not** drop the
     fingerprint to force the write through.
4. Same shape for `updateTrigger` (`{triggerPath}`) and `updateVariable`
   (`{variablePath}`).

## Revert (undo an unpublished workspace edit)

- **`revertTag`** — `POST /tagmanager/v2/{tagPath}:revert`. Discards the workspace's
  changes to that tag and restores it to the state in the container's currently
  published version. Same for **`revertTrigger`** (`{triggerPath}:revert`) and
  **`revertVariable`** (`{variablePath}:revert`).
- Revert only reaches **unpublished** workspace changes. Once a version is published,
  revert does nothing useful — to undo live, publish the previous container version
  instead (see the audit skill).

## Rules

- **`fingerprint` is mandatory in practice.** Omitting it turns an optimistic-locked
  write into a last-writer-wins overwrite of a colleague's edit.
- **PUT is destructive by omission.** Round-trip the full entity.
- **No idempotency key.** A retried `updateTag` after a network timeout is safe only
  because the fingerprint will have moved — the second attempt 409s rather than
  double-applying. That is the whole safety mechanism; do not defeat it.
- **Errors**: `409` = re-read and retry, `400` = bad body/fingerprint format,
  `403 usageLimits` = backoff. See `errors/google-tag-manager-problem-types.yml`.
