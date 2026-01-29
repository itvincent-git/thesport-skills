---
name: football-season-standing-docs
description: Detailed documentation for the Football Season Standing (Newest Season) API endpoint, including authentication, request parameters, and response field descriptions for league tables, promotions, and relegations.
---

# Football Season Standing API Documentation

## Endpoint: Season Standing (Newest Season)

**URL:** `GET /v1/football/season/recent/table/detail`

This endpoint returns detailed league table (standings) data for the latest/newest season of a competition. It includes promotion/relegation zones and team performance metrics.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type   | Required | Description    |
|:------ |:------ |:-------- |:-------------- |
| `uuid` | string | Yes      | The Season ID. |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (object): Standings data wrapper.

#### Result Fields (`results`)

| Field        | Type  | Description                                                |
|:------------ |:----- |:---------------------------------------------------------- |
| `promotions` | array | List of promotion/relegation rules: `{ id, name, color }`. |
| `tables`     | array | List of standing tables (usually one, or one per group).   |

#### Table Object Fields (`results.tables[]`)

| Field      | Type    | Description                                  |
|:---------- |:------- |:-------------------------------------------- |
| `id`       | string  | Table ID.                                    |
| `stage_id` | string  | Stage ID.                                    |
| `group`    | integer | Group number (1-A, 2-B, etc. 0 if no group). |
| `rows`     | array   | List of team ranking rows.                   |

#### Standing Row Fields (`results.tables[].rows[]`)

| Field                | Type    | Description                              |
|:-------------------- |:------- |:---------------------------------------- |
| `team_id`            | string  | Team ID.                                 |
| `position`           | integer | Current rank in table.                   |
| `points`             | integer | Total points.                            |
| `total`              | integer | Total matches played.                    |
| `won`                | integer | Wins.                                    |
| `draw`               | integer | Draws.                                   |
| `loss`               | integer | Losses.                                  |
| `goals`              | integer | Goals scored.                            |
| `goals_against`      | integer | Goals conceded.                          |
| `goal_diff`          | integer | Goal difference.                         |
| `promotion_id`       | string  | ID mapping to `results.promotions` zone. |
| `home_total/won/...` | integer | Home performance metrics.                |
| `away_total/won/...` | integer | Away performance metrics.                |
| `deduct_points`      | integer | Points deducted by league (if any).      |
| `updated_at`         | integer | Unix timestamp of last update.           |

### Example Request

```bash
curl "https://api.thesports.com/v1/football/season/recent/table/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=SEASON_ID"
```
