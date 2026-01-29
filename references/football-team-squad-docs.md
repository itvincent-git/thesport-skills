---
name: football-team-squad-docs
description: Detailed documentation for the Football Team Lineup (Squad) API endpoint, including authentication, request parameters, and response field descriptions for current team rosters and jersey numbers.
---

# Football Team Lineup (Squad) API Documentation

## Endpoint: Team Lineup (Squad)

**URL:** `GET /v1/football/team/squad/list`

This endpoint returns the full player squad (roster) for teams. Supports both full and incremental updates based on time.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type    | Required | Description                                                                                  |
|:------ |:------- |:-------- |:-------------------------------------------------------------------------------------------- |
| `page` | integer | No       | Page number (starts at 1). Default is 100 records per page. Use for full updates.            |
| `time` | integer | No       | Unix timestamp. Returns records updated at or after this time. Recommended frequency: 1 min. |
| `uuid` | string  | No       | Filter by a specific Team ID.                                                                |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List of team squad objects.

#### Result Fields (`results[]`)

| Field        | Type    | Description                           |
|:------------ |:------- |:------------------------------------- |
| `id`         | string  | Team ID.                              |
| `team`       | object  | Team details: `{ id, name, logo }`.   |
| `squad`      | array   | List of players in the current squad. |
| `updated_at` | integer | Unix timestamp of last update.        |

#### Squad Player Object Fields (`results[].squad[]`)

| Field          | Type    | Description                     |
|:-------------- |:------- |:------------------------------- |
| `player`       | object  | Player details: `{ id, name }`. |
| `position`     | string  | Player position (F, M, D, G).   |
| `shirt_number` | integer | Jersey number.                  |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/team/squad/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/team/squad/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
