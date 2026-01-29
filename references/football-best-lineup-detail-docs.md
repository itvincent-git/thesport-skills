---
name: football-best-lineup-detail-docs
description: Detailed documentation for the Football Best Lineup Detail API endpoint, including authentication, request parameters, and response field descriptions for player positions and ratings in the best lineup of a round.
---

# Football Best Lineup Detail API Documentation

## Endpoint: Best Lineup Details
**URL:** `GET /v1/football/competition/best_lineup/detail`

This endpoint returns the specific player details for a "Best Lineup" (e.g., Team of the Week), including their positions on the pitch and match ratings.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | The Best Lineup ID (obtained from the Best Lineup List endpoint). |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP status code.
- **results** (object): Wrapper for lineup information and player details.

#### Result Fields (`results`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `info` | object | Header information about the lineup (ID, competition, season, stage, name, formation, etc.). |
| `detail` | array | List of players included in the best lineup. |

#### Lineup Detail Player Fields (`results.detail[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `team_id` | string | Team ID of the player. |
| `player_id` | string | Player ID. |
| `rating` | integer | Player match rating (scaled by 100, e.g., 760 = 7.60). |
| `location_x` | integer | Pitch x-coordinate (0-100). |
| `location_y` | integer | Pitch y-coordinate (0-100). |
| `position` | string | Player position category (F, M, D, G). |

### Usage Recommendations
- **Frequency:** 120 times/min (rate limit).

### Example Request

```bash
curl "https://api.thesports.com/v1/football/competition/best_lineup/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=LINEUP_ID"
```
