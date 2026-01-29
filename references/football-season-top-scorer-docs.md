---
name: football-season-top-scorer-docs
description: Detailed documentation for the Football Season Top Scorer (Newest Season) API endpoint, including authentication, request parameters, and response field descriptions for top goal scorers.
---

# Football Season Top Scorer API Documentation

## Endpoint: Season Top Scorer (Newest Season)

**URL:** `GET /v1/football/season/recent/shooter/stat`

This endpoint returns the top scorer list for the current/newest season. **Note:** Due to transfers, a player may appear multiple times if they scored for different teams.

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
- **results** (array): List of scorer statistics objects.

#### Scorer Object Fields (`results[]`)

| Field            | Type    | Description                                                              |
|:---------------- |:------- |:------------------------------------------------------------------------ |
| `position`       | integer | Rank in the scorer list.                                                 |
| `player`         | object  | Player details: `{ id, name, logo, position, country_id, nationality }`. |
| `team`           | object  | Team details: `{ id, name, logo }`.                                      |
| `goals`          | integer | Total goals scored.                                                      |
| `penalty`        | integer | Penalty goals.                                                           |
| `assists`        | integer | Total assists.                                                           |
| `minutes_played` | integer | Total minutes played.                                                    |
| `updated_at`     | integer | Unix timestamp of last update.                                           |

### Usage Recommendations

- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/season/recent/shooter/stat?user=YOUR_USER&secret=YOUR_SECRET&uuid=SEASON_ID"
```
