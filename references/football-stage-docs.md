---
name: football-stage-docs
description: Detailed documentation for the Football Stage API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Stage API Documentation

## Endpoint: Stage List

**URL:** `GET /v1/football/stage/list`

This endpoint returns full stage data (e.g., "Group Stage", "Final", "Regular Season"). Supports both full and incremental updates based on time.

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
- **results** (array): List of stage objects.

#### Stage Object Fields (`results[]`)

| Field         | Type    | Description                                   |
|:------------- |:------- |:--------------------------------------------- |
| `id`          | string  | Unique Stage ID.                              |
| `season_id`   | string  | ID of the season this stage belongs to.       |
| `name`        | string  | Stage name.                                   |
| `mode`        | integer | `1`: Points (League), `2`: Elimination (Cup). |
| `group_count` | integer | Total number of groups in this stage.         |
| `round_count` | integer | Total number of rounds in this stage.         |
| `order`       | integer | Sorting order of the stage within the season. |
| `updated_at`  | integer | Unix timestamp of the last update.            |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/stage/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/stage/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
