---
name: football-match-list-docs
description: Documentation for the Football Match List API endpoint, providing full and incremental updates for match data, including scores, status, incidents, and environment.
---

# Football Match List API Documentation

## Endpoint: Match
**URL:** `GET /v1/football/match/list`

Return full match data. Supports full sync (pagination) and incremental updates (timestamp).

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
| `id` | string | Match ID. |
| `season_id` | string | Season ID. |
| `competition_id` | string | Competition ID. |
| `home_team_id` | string | Home Team ID. |
| `away_team_id` | string | Away Team ID. |
| `status_id` | integer | Match status code. |
| `match_time` | integer | Match start time (Unix timestamp). |
| `venue_id` | string | Venue ID. |
| `referee_id` | string | Referee ID. |
| `home_scores` | array | [Regular, Halftime, Red, Yellow, Corners, Overtime, Penalty]. |
| `away_scores` | array | [Regular, Halftime, Red, Yellow, Corners, Overtime, Penalty]. |
| `coverage` | object | `{mlive: 1/0, lineup: 1/0}`. |
| `round` | object | Stage, group number, round number. |
| `environment` | object | Weather, pressure, temperature, wind, humidity. |
| `updated_at` | integer | Update timestamp. |

### Sync Recommendation
- **Incremental:** Recommended every 1 minute using the `time` parameter.
