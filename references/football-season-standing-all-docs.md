---
name: football-season-standing-all-docs
description: Documentation for the Football Season Standing (All Season) API endpoint, providing league table data including points, goals, and rankings across historical seasons.
---

# Football Season Standing (All Season) API Documentation

## Endpoint: Season standing(all season)
**URL:** `GET /v1/football/season/table/detail`

Return to season rankings data details.
Request times: 120 times/min.

### Authentication
Required for all requests.
- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | Season ID. |

### Response Structure
(Same as "Season standing(newest season)" `results[]` item structure, but returning an array of tables).

#### Result Fields (`results.tables[]`)
- `id` (string): Table ID.
- `conference`, `group`, `stage_id`.
- `rows` (array): List of team standings.
    - `team_id`, `points`, `position`, `total`, `won`, `draw`, `loss`, `goals`, `goals_against`, `goal_diff`, `home_*`, `away_*`.
    - `updated_at` (integer): Update time.
