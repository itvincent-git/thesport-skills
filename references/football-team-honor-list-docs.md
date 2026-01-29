---
name: football-team-honor-list-docs
description: Documentation for the Football Team Honor List API endpoint, tracking historical honors and trophies won by football teams.
---

# Football Team Honor List API Documentation

## Endpoint: Team honor
**URL:** `GET /v1/football/team/honor/list`

Return full team honor data. Supports full sync (pagination) and incremental updates (timestamp).

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
| `id` | string | Team ID. |
| `team` | object | Basic team info (`id`, `name`). |
| `honors` | array | List of honors won. |
| `updated_at` | integer | Update timestamp. |

#### Honor Item Fields (`results[].honors[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `honor` | object | Honor info (`id`, `name`). |
| `season` | string | Season year (e.g., "2020-2021"). |
| `competition_id` | string | Competition ID. |
| `season_id` | string | Season ID. |
