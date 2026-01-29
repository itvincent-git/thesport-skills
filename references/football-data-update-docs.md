---
name: football-data-update-docs
description: Detailed documentation for the Football Data Update API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Data Update API Documentation

## Endpoint: Data Update

**URL:** `GET /v1/football/data/update`

This endpoint returns a list of data IDs that have changed in the last 120 seconds. It is the primary mechanism for keeping your local database synchronized in real-time.

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

- **code** (integer): HTTP-like status code (e.g., 200).
- **results** (object): A map where keys are "Type IDs" (describing what kind of data changed) and values are arrays of changed objects.

#### Update Object Fields (`results[type_id][]`)

| Field         | Type    | Description                                                                     |
|:------------- |:------- |:------------------------------------------------------------------------------- |
| `match_id`    | string  | ID of the match that was updated (present for live scores, lineups, incidents). |
| `season_id`   | string  | ID of the season that was updated (present for standings, stats, brackets).     |
| `pub_time`    | integer | Publication time (present for rankings like FIFA).                              |
| `update_time` | integer | The timestamp of the update.                                                    |

### Usage Recommendations

- **Frequency:** Poll this endpoint every **20 seconds**.
- **Logic:**
  1. Call `data/update`.
  2. Iterate through the returned `results`.
  3. Identify the `type_id` (e.g., live score, odds, stats). *Note: Refer to "Status Code -> Data Update Type ID" in the full documentation for mapping IDs to specific endpoints.*
  4. Call the corresponding detail endpoint (e.g., `match/live/list` or `season/standing/list`) using the returned `match_id` or `season_id` to fetch the actual new data.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/data/update?user=YOUR_USER&secret=YOUR_SECRET"
```
