---
name: football-season-top-scorer-all-docs
description: Documentation for the Football Season Top Scorer (All Season) API endpoint, providing detailed goalscoring and assist data for players across historical seasons.
---

# Football Season Top Scorer (All Season) API Documentation

## Endpoint: Season top scorer(all season)
**URL:** `GET /v1/football/season/shooter/stat`

Return to the season scorer list details data.
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
(Same as "Season top scorer(newest season)" `results[]` item structure).

#### Result Fields (`results[]`)
- `position` (integer): Rank.
- `player` (object): Player info.
- `team` (object): Team info.
- `goals` (integer): Goals.
- `penalty` (integer): Penalties.
- `assists` (integer): Assists.
- `minutes_played` (integer): Minutes played.
- `updated_at` (integer): Update time.
