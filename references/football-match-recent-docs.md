---
name: football-match-recent-docs
description: Detailed documentation for the Football Match (Recent) API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Match (Recent) API Documentation

## Endpoint: Match List (Recent)

**URL:** `GET /v1/football/match/recent/list`

This endpoint returns match data updated within the last few days (limit: starting 30 days before today). Supports both full and incremental updates based on time.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type    | Required | Description                                                                                  |
|:------ |:------- |:-------- |:-------------------------------------------------------------------------------------------- |
| `page` | integer | No       | Page number (starts at 1). Default is 1000 records per page. Use for full updates.           |
| `time` | integer | No       | Unix timestamp. Returns records updated at or after this time. Recommended frequency: 1 min. |
| `uuid` | string  | No       | Filter by a specific unique identifier.                                                      |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP-like status code (e.g., 200).
- **query** (object): Metadata about the request.
- **results** (array): List of match objects.

#### Match Object Fields (`results[]`)

| Field            | Type    | Description                                                                                                        |
|:---------------- |:------- |:------------------------------------------------------------------------------------------------------------------ |
| `id`             | string  | Unique Match ID.                                                                                                   |
| `season_id`      | string  | ID of the season.                                                                                                  |
| `competition_id` | string  | ID of the competition.                                                                                             |
| `home_team_id`   | string  | ID of the home team.                                                                                               |
| `away_team_id`   | string  | ID of the away team.                                                                                               |
| `status_id`      | integer | Match status code (see Status Code -> Match Status).                                                               |
| `match_time`     | integer | Timestamp of match start.                                                                                          |
| `venue_id`       | string  | ID of the venue.                                                                                                   |
| `referee_id`     | string  | ID of the referee.                                                                                                 |
| `neutral`        | integer | `1`: Neutral ground, `0`: No.                                                                                      |
| `note`           | string  | Remarks/Notes.                                                                                                     |
| `home_scores`    | array   | Home scores: `[Regular, Half, Red, Yellow, Corners, Overtime, Penalty]`.                                           |
| `away_scores`    | array   | Away scores: `[Regular, Half, Red, Yellow, Corners, Overtime, Penalty]`.                                           |
| `home_position`  | string  | Home team league standing/position.                                                                                |
| `away_position`  | string  | Away team league standing/position.                                                                                |
| `coverage`       | object  | `{ "mlive": 1/0, "lineup": 1/0 }` (Has animation/lineup?).                                                         |
| `round`          | object  | `{ "stage_id": string, "group_num": int, "round_num": int }`.                                                      |
| `related_id`     | string  | ID of the other leg in a double-legged tie.                                                                        |
| `agg_score`      | array   | Aggregate score `[Home, Away]` (if applicable).                                                                    |
| `environment`    | object  | Weather info: `{ "weather": int, "pressure": string, "temperature": string, "wind": string, "humidity": string }`. |
| `tbd`            | integer | `1`: Time to be determined.                                                                                        |
| `has_ot`         | integer | `1`: Has overtime.                                                                                                 |
| `ended`          | integer | Timestamp of match end.                                                                                            |
| `team_reverse`   | integer | `1`: Home/Away reversed compared to official listing.                                                              |
| `loss`           | integer | `1`: Match decided by default/forfeit.                                                                             |
| `updated_at`     | integer | Unix timestamp of the last update.                                                                                 |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/match/recent/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/match/recent/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
