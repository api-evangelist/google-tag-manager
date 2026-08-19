---
name: Grant, adjust and revoke Tag Manager user permissions
description: Manage who can read, edit, approve and publish in a Tag Manager account and its containers — the access-governance flow for the v2 API.
api: openapi/google-tag-manager-user-permissions-api-openapi.yml
apis:
  - openapi/google-tag-manager-accounts-api-openapi.yml
  - openapi/google-tag-manager-user-permissions-api-openapi.yml
operations: [listAccounts, listUserPermissions, createUserPermission, getUserPermission, updateUserPermission, deleteUserPermission]
generated: '2026-08-13'
method: generated
source: openapi/ (Tag Manager API v2) + https://developers.google.com/tag-platform/tag-manager/api/v2/devguide
---

# Manage user permissions

Permissions are two-level: one **account-level** permission plus zero or more
**container-level** permissions, all carried on a single `userPermission` resource
keyed by the user's email address.

Every operation here requires
`https://www.googleapis.com/auth/tagmanager.manage.users`. This scope is the
highest-privilege scope in the API — it can grant another principal the ability to
publish to live traffic. Do not bundle it into a token issued for tag-editing work.

## Steps

1. **`listAccounts`** — `GET /tagmanager/v2/accounts` to get the account `path`.
2. **`listUserPermissions`** — `GET /tagmanager/v2/{parent}/user_permissions`,
   `parent` = the account path. Returns `userPermission[]`, each with
   `emailAddress`, `accountAccess.permission` and `containerAccess[]` of
   `{containerId, permission}`. Paginate with `pageToken`.
3. **`createUserPermission`** — `POST /tagmanager/v2/{parent}/user_permissions`.
   Body: `emailAddress`, `accountAccess: {permission: ...}`, and `containerAccess[]`
   entries per container. Create fails if the user already has a permission on the
   account — call step 2 first and branch to `updateUserPermission` instead.
4. **`getUserPermission`** — `GET /tagmanager/v2/{userPermissionPath}` to read one
   principal's current grants before changing them.
5. **`updateUserPermission`** — `PUT /tagmanager/v2/{userPermissionPath}` with the
   full permission object. This is a **replace**: a `containerAccess[]` you omit is a
   grant you revoked. Always read with step 4 and send back the modified whole.
   Note this operation takes **no `fingerprint` parameter** — unlike tags, triggers
   and variables, permission writes are last-writer-wins with no optimistic lock.
6. **`deleteUserPermission`** — `DELETE /tagmanager/v2/{userPermissionPath}` to
   remove the principal from the account entirely.

## Rules

- **Least privilege by container.** Grant account access at the lowest level that
  works and scope real capability per container in `containerAccess[]`, rather than
  handing out account-wide edit rights.
- **`publish` is the crown jewel.** A container-level publish permission lets that
  user change what runs on production sites. Treat granting it as an escalation
  requiring human approval.
- **No fingerprint, no undo.** Steps 5 and 6 have no optimistic-concurrency guard and
  no confirmation — the developer guide's "no warnings, no confirmations, and no
  undo" warning applies most sharply here. Snapshot `listUserPermissions` output
  before a bulk change so the prior state can be restored by hand.
- **No idempotency key.** Re-running `createUserPermission` after a timeout errors
  rather than duplicating, but confirm with step 2 rather than assuming.
- Errors: `403 insufficientPermissions` means your token lacks
  `tagmanager.manage.users`; `403` with domain `usageLimits` is quota — back off.
  See `errors/google-tag-manager-problem-types.yml`.
