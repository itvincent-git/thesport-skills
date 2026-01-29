---
name: football-season-docs
description: Detailed documentation for the Football Season API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Season API Documentation

## Endpoint: Season List

**URL:** `GET /v1/football/season/list`

This endpoint returns full season data. Supports both full and incremental updates based on time.

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
- **results** (array): List of season objects.

#### Season Object Fields (`results[]`)

| Field              | Type    | Description                                   |
|:------------------ |:------- |:--------------------------------------------- |
| `id`               | string  | Unique Season ID.                             |
| `competition_id`   | string  | ID of the competition this season belongs to. |
| `year`             | string  | Season year label (e.g., "2023-2024").        |
| `has_player_stats` | integer | `1`: Has player stats, `0`: No.               |
| `has_team_stats`   | integer | `1`: Has team stats, `0`: No.                 |
| `has_table`        | integer | `1`: Has standings table, `0`: No.            |
| `is_current`       | integer | `1`: Current/Latest season, `0`: Historical.  |
| `start_time`       | integer | Season start timestamp.                       |
| `end_time`         | integer | Season end timestamp.                         |
| `updated_at`       | integer | Unix timestamp of the last update.            |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/season/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/season/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
