---
name: football-match-lineup-docs
description: Detailed documentation for the Football Single Match Lineup API endpoint, including authentication, request parameters, and response field descriptions for lineups, coordinates, and player incidents.
---

# Football Single Match Lineup API Documentation

## Endpoint: Single Match Lineup

**URL:** `GET /v1/football/match/lineup/detail`

This endpoint returns detailed lineup data for a single match, including starting players, substitutes, formations, coordinates, and player-specific incidents.

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
- **results** (object): Lineup and injury data.

#### Result Fields (`results`)

| Field            | Type    | Description                                                     |
|:---------------- |:------- |:--------------------------------------------------------------- |
| `confirmed`      | integer | `1`: Official lineup, `0`: Probable/Unofficial.                 |
| `home_formation` | string  | Home team formation (e.g., "4-4-2").                            |
| `away_formation` | string  | Away team formation.                                            |
| `coach_id`       | object  | `{ "home": string, "away": string }`.                           |
| `lineup`         | object  | Contains `home` and `away` arrays of player objects.            |
| `injury`         | object  | Contains `home` and `away` arrays of injured/suspended players. |

#### Player Object Fields (`results.lineup.home/away[]`)

| Field          | Type    | Description                                                               |
|:-------------- |:------- |:------------------------------------------------------------------------- |
| `id`           | string  | Player ID.                                                                |
| `first`        | integer | `1`: Starter, `0`: Substitute.                                            |
| `captain`      | integer | `1`: Captain, `0`: No.                                                    |
| `name`         | string  | Player name.                                                              |
| `shirt_number` | integer | Jersey number.                                                            |
| `position`     | string  | Position category (F, M, D, G).                                           |
| `x`            | integer | X-coordinate (0-100). Home origin: Top-Left. Away origin: Bottom-Right.   |
| `y`            | integer | Y-coordinate (0-100).                                                     |
| `rating`       | string  | Player match rating (0-10).                                               |
| `incidents`    | array   | Player events (goals, cards, etc.). See `football-realtime-data-docs.md`. |

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/lineup/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
