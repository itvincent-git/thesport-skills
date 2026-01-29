---
name: football-player-honor-list-docs
description: Documentation for the Football Player Honor List API endpoint, tracking historical awards and honors won by players.
---

# Football Player Honor List API Documentation

## Endpoint: Player honor
**URL:** `GET /v1/football/player/honor/list`

Return full player honor data. Supports full sync (pagination) and incremental updates (timestamp).

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
| `id` | string | Player ID. |
| `player` | object | Basic player info (`id`, `name`). |
| `honors` | array | List of honors won. |
| `updated_at` | integer | Update timestamp. |

#### Honor Item Fields (`results[].honors[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `honor` | object | Honor info (`id`, `name`). |
| `season` | string | Season year. |
| `team_id` | string | Team ID when won. |
| `competition_id` | string | Competition ID. |
| `season_id` | string | Season ID. |
| `country_id` | string | Country ID (optional). |
