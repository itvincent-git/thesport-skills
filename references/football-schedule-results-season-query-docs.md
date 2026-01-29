---
name: football-schedule-results-season-query-docs
description: Documentation for the Football Schedule and Results (Season Query) API endpoint, providing full schedule and result data for a specific season.
---

# Football Schedule and Results (Season Query) API Documentation

## Endpoint: Schedule and Results - season query(all season)
**URL:** `GET /v1/football/match/season`

Returns the full schedule and result data of the query season.
Request times: 120 times/min.
Note: If you get the full data from the Match interface, this interface does not need to be obtained again.

### Authentication
Required for all requests.
- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | Season ID. |

### Response Structure
(Same as Match List `results[]` item structure, but returning an array of matches for the season).

#### Result Fields (`results[]`)
- `id` (string): Match ID.
- `season_id` (string): Season ID.
- `competition_id` (string): Competition ID.
- `home_team_id` (string): Home Team ID.
- `away_team_id` (string): Away Team ID.
- `status_id` (integer): Match status.
- `match_time` (integer): Match time.
- `venue_id` (string): Venue ID.
- `referee_id` (string): Referee ID.
- `home_scores` (array): Home scores.
- `away_scores` (array): Away scores.
- `coverage` (object): Coverage info.
- `round` (object): Round info.
- `environment` (object): Environment info.
- `updated_at` (integer): Update time.
