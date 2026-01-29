---
name: football-historical-player-stats-docs
description: Detailed documentation for the Football Player Statistics (Historical Matches) API endpoint, including authentication, request parameters, and response field descriptions for exhaustive player performance metrics in completed matches.
---

# Football Historical Player Statistics API Documentation

## Endpoint: Player Statistics (Historical Matches)

**URL:** `GET /v1/football/match/player_stats/detail`

This endpoint returns exhaustive player statistics for completed historical matches.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type   | Required | Description   |
|:------ |:------ |:-------- |:------------- |
| `uuid` | string | Yes      | The Match ID. |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List of player statistics objects for the match.

#### Player Statistics Object Fields (`results[]`)

*The field structure is identical to the **Match Player Statistics** endpoint.*

Key metrics include:

- `goals`, `assists`, `minutes_played`, `rating`.
- `shots`, `shots_on_target`, `dribble_succ`, `passes_accuracy`.
- `tackles`, `interceptions`, `clearances`, `saves` (GK).
- `aerial_won`, `duel_won`, `poss_losts`.

*For the complete field list, refer to `football-player-match-stats-docs.md`.*

### Usage Recommendations

- **Request Limit:** Matches within **30 days** before today.
- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/player_stats/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
