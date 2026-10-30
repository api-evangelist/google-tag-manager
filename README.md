# Google Tag Manager

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Google Tag Manager is a tag management system that lets teams deploy and update measurement codes and related code fragments — collectively known as tags — on a website, mobile app, or server-side container without editing site code on every change. The Tag Manager API v2 exposes that configuration programmatically: accounts, containers, workspaces, tags, triggers, variables, container versions, and user permissions, across web, iOS, Android, AMP, and server-side usage contexts. Changes are staged in a workspace, frozen into an immutable container version, and then published to live traffic, with fingerprint-based optimistic concurrency guarding every write. Access is OAuth 2.0 only, with seven granular scopes separating read, edit, publish, and user-management rights.

**Areas:** Analytics · Conversion Tracking · Marketing · Tag Management · Tracking

## Google Tag Manager on APIs.io

Everything profiled for Google Tag Manager is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/google-tag-manager/](https://apis.io/providers/google-tag-manager/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [Google Tag Manager Server-side Tagging API](https://apis.io/apis/google-tag-manager/google-tag-manager-server-side-tagging-api/) — The Server-side Tagging API provides APIs for building custom tags, clients, and variables that run in a server-side container, enabling server-to-server…
- [Google Tag Manager Accounts API](https://apis.io/apis/google-tag-manager/google-tag-manager-accounts-api/) — Operations for managing Google Tag Manager accounts.
- [Google Tag Manager Containers API](https://apis.io/apis/google-tag-manager/google-tag-manager-containers-api/) — Operations for managing containers within a Google Tag Manager account.
- [Google Tag Manager Triggers API](https://apis.io/apis/google-tag-manager/google-tag-manager-triggers-api/) — Operations for managing triggers within a workspace that control when tags fire.
- [Google Tag Manager User Permissions API](https://apis.io/apis/google-tag-manager/google-tag-manager-user-permissions-api/) — Operations for managing user permissions on Google Tag Manager accounts.
- [Google Tag Manager Variables API](https://apis.io/apis/google-tag-manager/google-tag-manager-variables-api/) — Operations for managing variables within a workspace that provide dynamic values to tags and triggers.
- [Google Tag Manager Versions API](https://apis.io/apis/google-tag-manager/google-tag-manager-versions-api/) — Operations for managing container versions, including publishing and rollback.
- [Google Tag Manager Workspaces API](https://apis.io/apis/google-tag-manager/google-tag-manager-workspaces-api/) — Operations for managing workspaces within a container, including version creation and conflict resolution.
- [Google Tag Manager Tag Manager API](https://apis.io/apis/google-tag-manager/google-tag-manager-tag-manager-api/) — The Tag Manager API from Google Tag Manager — 3 operation(s) for tag manager.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (12)

Multi-step workflows that chain operations into a business task.

- [Google Tag Manager Audit Container Versions](https://apis.io/arazzos/google-tag-manager/google-tag-manager-audit-container-versions-workflow/)
- [Google Tag Manager Bootstrap a Live Container](https://apis.io/arazzos/google-tag-manager/google-tag-manager-bootstrap-live-container-workflow/)
- [Google Tag Manager Build and Publish a Tag End to End](https://apis.io/arazzos/google-tag-manager/google-tag-manager-build-and-publish-tag-workflow/)
- [Google Tag Manager Grant a User Permission](https://apis.io/arazzos/google-tag-manager/google-tag-manager-grant-user-permission-workflow/)
- [Google Tag Manager Inspect the Live Container Version](https://apis.io/arazzos/google-tag-manager/google-tag-manager-inspect-live-version-workflow/)
- [Google Tag Manager List and Get a Workspace](https://apis.io/arazzos/google-tag-manager/google-tag-manager-list-and-get-workspace-workflow/)
- [Google Tag Manager Provision a Tagged Container](https://apis.io/arazzos/google-tag-manager/google-tag-manager-provision-tagged-container-workflow/)
- [Google Tag Manager Safely Update a Tag](https://apis.io/arazzos/google-tag-manager/google-tag-manager-safe-update-tag-workflow/)
- [Google Tag Manager Sync and Version a Workspace](https://apis.io/arazzos/google-tag-manager/google-tag-manager-sync-and-version-workspace-workflow/)
- [Google Tag Manager Wire a Trigger-Fired Tag](https://apis.io/arazzos/google-tag-manager/google-tag-manager-trigger-fired-tag-workflow/)
- [Google Tag Manager Build a Variable-Backed Tag](https://apis.io/arazzos/google-tag-manager/google-tag-manager-variable-backed-tag-workflow/)
- [Google Tag Manager Version and Publish a Workspace](https://apis.io/arazzos/google-tag-manager/google-tag-manager-version-and-publish-workspace-workflow/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [google-tag-manager](https://apis.io/servers/google-tag-manager/google-tag-manager/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Google Tag Manager Agentic Access](https://apis.io/agentic-access/google-tag-manager/google-tag-manager-agentic-access/)

#### JSON Schema (39)

The data models the API reads and writes.

- [Google Tag Manager Container](https://apis.io/schemas/google-tag-manager/google-tag-manager-container/)
- [Account](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-account/)
- [AccountAccess](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-account-access/)
- [AccountFeatures](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-account-features/)
- [Condition](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-condition/)
- [ConsentSettings](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-consent-settings/)
- [Container](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-container/)
- [ContainerAccess](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-container-access/)
- [ContainerFeatures](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-container-features/)
- [ContainerVersion](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-container-version/)
- [ContainerVersionHeader](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-container-version-header/)
- [CreateContainerVersionRequestVersionOptions](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-create-container-version-request-version-options/)
- [CreateContainerVersionResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-create-container-version-response/)
- [Entity](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-entity/)
- [FormatValue](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-format-value/)
- [GetWorkspaceStatusResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-get-workspace-status-response/)
- [ListAccountsResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-accounts-response/)
- [ListContainerVersionsResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-container-versions-response/)
- [ListContainersResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-containers-response/)
- [ListTagsResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-tags-response/)
- [ListTriggersResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-triggers-response/)
- [ListUserPermissionsResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-user-permissions-response/)
- [ListVariablesResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-variables-response/)
- [ListWorkspacesResponse](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-list-workspaces-response/)
- [MergeConflict](https://apis.io/schemas/google-tag-manager/google-tag-manager-v2-merge-conflict/)
- …and 14 more published on APIs.io

#### JSON Structure (38)

Data models expressed in JSON Structure.

- [Google Tag Manager V2 Account Access Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-account-access-structure/)
- [Google Tag Manager V2 Account Features Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-account-features-structure/)
- [Google Tag Manager V2 Account Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-account-structure/)
- [Google Tag Manager V2 Condition Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-condition-structure/)
- [Google Tag Manager V2 Consent Settings Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-consent-settings-structure/)
- [Google Tag Manager V2 Container Access Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-container-access-structure/)
- [Google Tag Manager V2 Container Features Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-container-features-structure/)
- [Google Tag Manager V2 Container Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-container-structure/)
- [Google Tag Manager V2 Container Version Header Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-container-version-header-structure/)
- [Google Tag Manager V2 Container Version Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-container-version-structure/)
- [Google Tag Manager V2 Create Container Version Request Version Options Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-create-container-version-request-version-options-structure/)
- [Google Tag Manager V2 Create Container Version Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-create-container-version-response-structure/)
- [Google Tag Manager V2 Entity Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-entity-structure/)
- [Google Tag Manager V2 Format Value Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-format-value-structure/)
- [Google Tag Manager V2 Get Workspace Status Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-get-workspace-status-response-structure/)
- [Google Tag Manager V2 List Accounts Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-accounts-response-structure/)
- [Google Tag Manager V2 List Container Versions Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-container-versions-response-structure/)
- [Google Tag Manager V2 List Containers Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-containers-response-structure/)
- [Google Tag Manager V2 List Tags Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-tags-response-structure/)
- [Google Tag Manager V2 List Triggers Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-triggers-response-structure/)
- [Google Tag Manager V2 List User Permissions Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-user-permissions-response-structure/)
- [Google Tag Manager V2 List Variables Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-variables-response-structure/)
- [Google Tag Manager V2 List Workspaces Response Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-list-workspaces-response-structure/)
- [Google Tag Manager V2 Merge Conflict Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-merge-conflict-structure/)
- [Google Tag Manager V2 Parameter Structure](https://apis.io/json-structure/google-tag-manager/google-tag-manager-v2-parameter-structure/)
- …and 13 more published on APIs.io

#### JSON-LD (2)

Linked-data contexts for the provider's vocabulary.

- [Google Tag Manager Context](https://apis.io/jsonld/google-tag-manager/google-tag-manager-context/)
- [Google Tag Manager V2 Context](https://apis.io/jsonld/google-tag-manager/google-tag-manager-v2-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [google-tag-manager API Vocabulary](https://apis.io/vocabularies/google-tag-manager/google-tag-manager-vocabulary/)

#### Examples (38)

Example requests and responses.

- [Google Tag Manager V2 Account Access Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-account-access-example/)
- [Google Tag Manager V2 Account Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-account-example/)
- [Google Tag Manager V2 Account Features Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-account-features-example/)
- [Google Tag Manager V2 Condition Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-condition-example/)
- [Google Tag Manager V2 Consent Settings Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-consent-settings-example/)
- [Google Tag Manager V2 Container Access Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-container-access-example/)
- [Google Tag Manager V2 Container Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-container-example/)
- [Google Tag Manager V2 Container Features Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-container-features-example/)
- [Google Tag Manager V2 Container Version Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-container-version-example/)
- [Google Tag Manager V2 Container Version Header Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-container-version-header-example/)
- [Google Tag Manager V2 Create Container Version Request Version Options Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-create-container-version-request-version-options-example/)
- [Google Tag Manager V2 Create Container Version Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-create-container-version-response-example/)
- [Google Tag Manager V2 Entity Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-entity-example/)
- [Google Tag Manager V2 Format Value Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-format-value-example/)
- [Google Tag Manager V2 Get Workspace Status Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-get-workspace-status-response-example/)
- [Google Tag Manager V2 List Accounts Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-accounts-response-example/)
- [Google Tag Manager V2 List Container Versions Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-container-versions-response-example/)
- [Google Tag Manager V2 List Containers Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-containers-response-example/)
- [Google Tag Manager V2 List Tags Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-tags-response-example/)
- [Google Tag Manager V2 List Triggers Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-triggers-response-example/)
- [Google Tag Manager V2 List User Permissions Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-user-permissions-response-example/)
- [Google Tag Manager V2 List Variables Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-variables-response-example/)
- [Google Tag Manager V2 List Workspaces Response Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-list-workspaces-response-example/)
- [Google Tag Manager V2 Merge Conflict Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-merge-conflict-example/)
- [Google Tag Manager V2 Parameter Example](https://apis.io/examples/google-tag-manager/google-tag-manager-v2-parameter-example/)
- …and 13 more published on APIs.io

#### Collections (10)

Postman and Open Collection request collections.

- [Google Tag Manager Accounts API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-accounts-api/)
- [Google Tag Manager API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-api-v2/)
- [Google Tag Manager Accounts Containers API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-containers-api/)
- [Google Tag Manager Accounts Tagmanager API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-tagmanager-api/)
- [Google Tag Manager Accounts Triggers API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-triggers-api/)
- [Google Tag Manager Accounts User Permissions API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-user-permissions-api/)
- [Google Tag Manager Accounts Variables API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-variables-api/)
- [Google Tag Manager Accounts Versions API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-versions-api/)
- [Google Tag Manager Accounts Workspaces API](https://apis.io/collections/google-tag-manager/open-google-tag-manager-workspaces-api/)
- [Google Tag Manager API](https://apis.io/collections/google-tag-manager/postman-google-tag-manager-api-v2/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [Google Tag Manager Accounts Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-accounts-api-overlay/)
- [Google Tag Manager Containers Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-containers-api-overlay/)
- [Google Tag Manager Tagmanager Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-tagmanager-api-overlay/)
- [Google Tag Manager Triggers Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-triggers-api-overlay/)
- [Google Tag Manager User Permissions Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-user-permissions-api-overlay/)
- [Google Tag Manager Variables Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-variables-api-overlay/)
- [Google Tag Manager Versions Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-versions-api-overlay/)
- [Google Tag Manager Workspaces Api Overlay](https://apis.io/overlays/google-tag-manager/google-tag-manager-workspaces-api-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Google Tag Manager — jsonschema rules](https://apis.io/rules/google-tag-manager/google-tag-manager-jsonschema-spectral-rules/)
- [Google Tag Manager API Rules](https://apis.io/rules/google-tag-manager/google-tag-manager-spectral-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Google Tag Manager Authentication](https://apis.io/security/google-tag-manager/google-tag-manager-authentication/)
- [Google Tag Manager Domain Security](https://apis.io/security/google-tag-manager/google-tag-manager-domain-security/)
- [Google Tag Manager Trust Center](https://apis.io/security/google-tag-manager/google-tag-manager-trust-center/)
- [Google Tag Manager Vulnerability Disclosure](https://apis.io/security/google-tag-manager/google-tag-manager-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Google Tag Manager Scopes](https://apis.io/scopes/google-tag-manager/google-tag-manager-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Google Tag Manager Plans Pricing](https://apis.io/plans/google-tag-manager/google-tag-manager-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Google Tag Manager Rate Limits](https://apis.io/rate-limits/google-tag-manager/google-tag-manager-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Google Tag Manager Finops](https://apis.io/finops/google-tag-manager/google-tag-manager-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.google.com/)
- [Documentation](https://developers.google.com/tag-platform/tag-manager)
- [Getting started](https://developers.google.com/tag-platform/tag-manager/api/v2/devguide)
- [API reference](https://developers.google.com/tag-platform/tag-manager/api/reference/rest)
- [Pricing](https://marketingplatform.google.com/about/tag-manager/)
- [Support](https://support.google.com/tagmanager)
- [Changelog](https://support.google.com/tagmanager/answer/4620708)
- [Blog](https://blog.google/products/marketingplatform/)
- [Security](https://g.co/vrp)
- [Compliance](https://support.google.com/marketingplatform/answer/9013962)
- [Terms of service](https://policies.google.com/terms)
- [Privacy policy](https://policies.google.com/privacy)
- [GitHub](https://github.com/googleapis)

## API Evangelist rating

**Kin Score 63.6** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.4 |
| Contract quality | 62.3 |
| Contract governance | 31.8 |
| Operational transparency | 34.2 |
| Developer ergonomics | 69.6 |
| Access clarity | 73.7 |

**Agent readiness 38.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 40.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/google-tag-manager/](https://apis.io/providers/google-tag-manager/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Google Tag Manager: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/google-tag-manager/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
