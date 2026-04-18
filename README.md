# Google Tag Manager (google-tag-manager)
Google Tag Manager is a tag management system that allows you to quickly and easily update measurement codes and related code fragments collectively known as tags on your website or mobile app.

**URL:** [Visit APIs.json URL](https://tagmanager.google.com/)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Analytics, Conversion Tracking, Marketing, Tag Management, Tracking

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-04-18

## APIs

### Google Tag Manager API
The Tag Manager API allows clients to access and modify container and tag configuration.

**Human URL:** [https://developers.google.com/tag-platform/tag-manager/api/v2](https://developers.google.com/tag-platform/tag-manager/api/v2)

#### Tags:

 - Analytics, Containers, Permissions, Tag Management, Triggers, Variables, Versions, Workspaces

#### Properties

- [OpenAPI](openapi/google-tag-manager-api-v2-openapi.yml)
- [JSONSchema](json-schema/google-tag-manager-container-schema.json)
- [JSONLD](json-ld/google-tag-manager-context.jsonld)
- [Documentation](https://developers.google.com/tag-platform/tag-manager/api/v2)
- [APIReference](https://developers.google.com/tag-platform/tag-manager/api/reference/rest)
- [Authentication](https://developers.google.com/tag-platform/tag-manager/api/v2/authorization)
- [GettingStarted](https://developers.google.com/tag-platform/tag-manager/api/v2/devguide)
- [SDK](https://developers.google.com/tag-platform/tag-manager/api/v2/libraries)
- [RateLimits](https://developers.google.com/tag-platform/tag-manager/api/v2/limits-quotas)
- [ChangeLog](https://support.google.com/tagmanager/answer/4620708)

### Google Tag Manager Server-side Tagging API
The Server-side Tagging API provides APIs for building custom tags, clients, and variables that run in a server-side container, enabling server-to-server data collection and processing.

**Human URL:** [https://developers.google.com/tag-platform/tag-manager/server-side](https://developers.google.com/tag-platform/tag-manager/server-side)

#### Tags:

 - Analytics, Data Collection, Privacy, Server-Side Tagging, Tag Management

#### Properties

- [Documentation](https://developers.google.com/tag-platform/tag-manager/server-side)
- [APIReference](https://developers.google.com/tag-platform/tag-manager/server-side/api)
- [GettingStarted](https://developers.google.com/tag-platform/tag-manager/server-side/intro)
- [ReleaseNotes](https://developers.google.com/tag-platform/tag-manager/server-side/release-notes)

## Common Properties

- [Portal](https://developers.google.com/tag-platform)
- [GettingStarted](https://developers.google.com/tag-platform/tag-manager/api/v2/devguide)
- [Authentication](https://developers.google.com/tag-platform/tag-manager/api/v2/authorization)
- [Documentation](https://developers.google.com/tag-platform/tag-manager)
- [Blog](https://blog.google/products/marketingplatform/)
- [SDK](https://developers.google.com/tag-platform/tag-manager/api/v2/libraries)
- [Support](https://support.google.com/tagmanager)
- [StatusPage](https://status.cloud.google.com/)
- [TermsOfService](https://policies.google.com/terms)
- [PrivacyPolicy](https://policies.google.com/privacy)
- [SignUp](https://tagmanager.google.com/)
- [Login](https://tagmanager.google.com/)
- [RateLimits](https://developers.google.com/tag-platform/tag-manager/api/v2/limits-quotas)
- [ChangeLog](https://support.google.com/tagmanager/answer/4620708)
- [StackOverflow](https://stackoverflow.com/questions/tagged/google-tag-manager)
- [YouTube](https://www.youtube.com/googlemarketingplatform)

## Features

| Name | Description |
|------|-------------|
| Account Management | List and manage Google Tag Manager accounts with full access control. |
| Container Management | Create, update, delete, and configure containers for web, mobile, and server-side tagging. |
| Workspace Management | Create and manage workspaces for collaborative tag development with conflict resolution. |
| Tag Configuration | Create, update, delete, and revert tags with full parameter and firing trigger configuration. |
| Trigger Configuration | Define triggers that control when and how tags fire based on events and conditions. |
| Variable Management | Create and manage variables that provide dynamic values to tags and triggers. |
| Version Control | Create, publish, and manage container versions with rollback capabilities. |
| User Permissions | Manage user access and permissions at the account and container level. |
| Server-Side Tagging | Build custom server-side tags, clients, and variables for server-to-server data collection. |
| Data Layer | Structured data layer for passing information between your website and Tag Manager. |

## Use Cases

| Name | Description |
|------|-------------|
| Marketing Tag Deployment | Deploy and manage marketing and analytics tags without modifying website code. |
| Conversion Tracking | Track conversions across multiple advertising platforms with centralized tag management. |
| Privacy Compliance | Implement consent-based tag firing and data collection policies for GDPR and CCPA compliance. |
| A/B Testing | Deploy and manage A/B testing tags and experiment configurations across web properties. |
| Server-Side Data Collection | Process data server-side for improved performance, accuracy, and privacy compliance. |

## Integrations

| Name | Description |
|------|-------------|
| Google Analytics | Native integration with Google Analytics 4 for event tracking and measurement. |
| Google Ads | Deploy Google Ads conversion tracking and remarketing tags with built-in templates. |
| Google Marketing Platform | Integrate with Campaign Manager, Display & Video 360, and Search Ads 360. |
| Facebook Pixel | Deploy and manage Facebook Pixel tracking with community template support. |
| Consent Management Platforms | Integrate with consent management platforms for privacy-compliant tag firing. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [Google Tag Manager API v2](openapi/google-tag-manager-api-v2-openapi.yml)

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [Tag Manager API](capabilities/shared/tag-manager.yaml) — 22 operations for account, container, tag, trigger, and variable management

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Tag Deployment Management](capabilities/tag-deployment-management.yaml) | Tag Manager | 21 | Marketing Technologist / Web Analytics Engineer |

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
