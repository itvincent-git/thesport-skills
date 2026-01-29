---
name: football-realtime-standing-docs
description: Detailed documentation for the Football Real-time Standings API endpoint, including authentication, request parameters, and response field descriptions for live ranking changes during the season.
---

# Football Real-time Standings API Documentation

## Endpoint: Real-time Standings

**URL:** `GET /v1/football/table/live`

This endpoint returns real-time updates to season standings within the last 10 minutes. Use this to reflect instant rank changes as goals are scored.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name     | Type   | Required | Description |
|:-------- |:------ |:-------- |:----------- |
| `user`   | string | Yes      | Username.   |
| `secret` | string | Yes      | API Key.    |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List of real-time standings objects.

#### Result Fields (`results[]`)

| Field        | Type    | Description                                                |
|:------------ |:------- |:---------------------------------------------------------- |
| `season_id`  | string  | Season ID.                                                 |
| `promotions` | array   | List of promotion/relegation zones: `{ id, name, color }`. |
| `tables`     | array   | List of standings tables. Each table contains `rows`.      |
| `updated_at` | integer | Unix timestamp of last update.                             |

#### Standing Row Fields (`results[].tables[].rows[]`)

*The field structure is identical to the **Season Standing** endpoint.*

Includes: `team_id`, `position`, `points`, `total`, `won`, `draw`, `loss`, `goals`, `goals_against`, `goal_diff`, and home/away splits.

*For detailed field descriptions, refer to `football-season-standing-docs.md`.*

### Usage Recommendations

- **Frequency:** Poll every **1 to 5 minutes**.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/table/live?user=YOUR_USER&secret=YOUR_SECRET"
```
