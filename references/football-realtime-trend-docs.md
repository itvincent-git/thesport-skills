---
name: football-realtime-trend-docs
description: Detailed documentation for the Football Real-time Match Trend API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Real-time Match Trend API Documentation

## Endpoint: Real-time Match Trends

**URL:** `GET /v1/football/match/trend/live`

This endpoint returns home and away team trend details (momentum/pressure) for live matches. Positive values indicate home team dominance, negative values indicate away team dominance.

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
- **results** (array): List of trend objects.

#### Trend Object Fields (`results[]`)

| Field         | Type    | Description                                                                                                                                                                                                                                |
|:------------- |:------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `match_id`    | string  | Unique Match ID.                                                                                                                                                                                                                           |
| `trend`       | object  | Trend data wrapper.                                                                                                                                                                                                                        |
| `trend.count` | integer | Number of halves/periods (usually 2).                                                                                                                                                                                                      |
| `trend.per`   | integer | Duration per half (e.g., 45 minutes).                                                                                                                                                                                                      |
| `trend.data`  | array   | Array of arrays containing trend values. <br> Example: `[[FirstHalfData], [SecondHalfData]]`. <br> Inner array format: `[Minute, HomeValue, AwayValue]` or `[Minute, Value]`. <br> **Note:** Home team is positive, away team is negative. |

### Usage Recommendations

- **Frequency:** Poll every **1 minute**.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/trend/live?user=YOUR_USER&secret=YOUR_SECRET"
```
