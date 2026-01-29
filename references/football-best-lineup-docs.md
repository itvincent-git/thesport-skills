---
name: football-best-lineup-docs
description: Detailed documentation for the Football Best Lineup (Season/Round) API endpoint, including authentication, request parameters, and response field descriptions for the best performing team of the round.
---

# Football Best Lineup API Documentation

## Endpoint: Best Lineup
**URL:** `GET /v1/football/competition/best_lineup/list`

This endpoint returns the "Team of the Week" or best lineup data for all season rounds. Supports both full and incremental updates based on time.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `page` | integer | No | Page number (starts at 1). Default is 1000 records per page. Use for full updates. |
| `time` | integer | No | Unix timestamp. Returns records updated at or after this time. Recommended frequency: 1 min. |
| `uuid` | string | No | Filter by a specific Best Lineup ID. |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP status code.
- **results** (array): List of best lineup objects.

#### Best Lineup Object Fields (`results[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | string | Best Lineup ID. |
| `competition_id` | string | Competition ID. |
| `season_id` | string | Season ID. |
| `stage_id` | string | Stage ID. |
| `name` | string | Name of the lineup (e.g., "Round 15 Best XI"). |
| `formation` | string | Formation used (e.g., "4-3-3"). |
| `update_time` | integer | Data release time. |
| `updated_at` | integer | Unix timestamp of last update. |

### Usage Recommendations
- **Frequency:** 1 min/time.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/competition/best_lineup/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```
