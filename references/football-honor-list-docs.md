---
name: football-honor-list-docs
description: Documentation for the Football Honor List API endpoint, providing a list of all football honors (trophies, awards).
---

# Football Honor List API Documentation

## Endpoint: Honor list
**URL:** `GET /v1/football/honor/list`

Return full honor data. Supports full sync (pagination) and incremental updates (timestamp).

### Authentication
Required for all requests.
- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| `page` | integer | Page number for full sync (starting from 1). |
| `time` | integer | Unix timestamp for incremental updates (returns records >= update time). |
| `uuid` | string | Query a specific record by ID. |

### Response Structure

#### Result Fields (`results[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | string | Honor ID. |
| `name` | string | Honor Name. |
| `logo` | string | Honor Logo URL. |
| `updated_at` | integer | Update timestamp. |

### Sync Recommendation
- **Incremental:** Recommended every 1 minute using the `time` parameter.
