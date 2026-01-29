---
name: football-historical-team-stats-docs
description: Detailed documentation for the Football Team Statistics (Historical Matches) API endpoint, including authentication, request parameters, and response field descriptions for exhaustive team performance metrics in completed matches.
---

# Football Historical Team Statistics API Documentation

## Endpoint: Team Statistics (Historical Matches)
**URL:** `GET /v1/football/match/team_stats/detail`

This endpoint returns exhaustive team statistics for completed historical matches.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | The Match ID. |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP status code.
- **results** (array): List containing the team statistics object for the match.

#### Team Statistics Object Fields (`results[]`)
*The field structure is identical to the **Match Team Statistics** endpoint.*

Key metrics include:
- `goals`, `assists`, `red_cards`, `yellow_cards`.
- `shots`, `shots_on_target`, `dribble_succ`, `passes_accuracy`.
- `corner_kicks`, `ball_possession`.
- `aerial_won`, `duel_won`, `poss_losts`.

*For the complete field list, refer to `football-team-match-stats-docs.md`.*

### Usage Recommendations
- **Request Limit:** Matches within **30 days** before today.
- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/team_stats/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
