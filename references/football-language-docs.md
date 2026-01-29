---
name: football-language-docs
description: Documentation for the Football Language API endpoint, providing multi-language translations for categories, countries, competitions, teams, players, and injury types.
---

# Football Language API Documentation

## Endpoint: Language
**URL:** `GET /v1/football/language/list`

Return full multi-language data (category, country/region, competition, team, player, injury). Supports full sync and incremental updates.

### Authentication
Required for all requests.
- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `page` | integer | No | Page number (default 1000). |
| `time` | integer | No | Unix timestamp for incremental updates. |
| `uuid` | string | No | Query by ID. |
| `type` | integer | Yes | List type: 1-category, 2-country/region, 3-competition, 4-team, 5-player, 6-injury. |

### Response Structure

#### Result Fields (`results[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | string | Data ID. |
| `name_*` | string | Name in specific language (e.g., `name_zh`, `name_en`). |
| `updated_at` | integer | Update timestamp. |
