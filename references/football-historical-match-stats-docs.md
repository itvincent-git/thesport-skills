---
name: football-historical-match-stats-docs
description: Detailed documentation for the Football Statistical Data (Historical Matches) API endpoint, including authentication, request parameters, and response field descriptions for scores, incidents, and technical statistics of completed matches.
---

# Football Historical Match Statistics API Documentation

## Endpoint: Statistical Data (Historical Matches)

**URL:** `GET /v1/football/match/live/history`

This endpoint returns full statistics (scores, incidents, technical stats) for completed matches.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type   | Required | Description   |
|:------ |:------ |:-------- |:------------- |
| `uuid` | string | Yes      | The Match ID. |

### Response Structure

The response structure is identical to the **Real-time Data** endpoint (`GET /v1/football/match/detail_live`).

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List containing the match data object.

#### Match Data Object Fields

- `id` (string): Match ID.
- `score` (array): Final scores.
- `stats` (array): Team technical statistics.
- `incidents` (array): Match event timeline.
- `tlive` (array): Text commentary.

*For detailed field descriptions, please refer to `football-realtime-data-docs.md`.*

### Usage Recommendations

- **Request Limit:** Matches within **30 days** before today.
- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/live/history?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
