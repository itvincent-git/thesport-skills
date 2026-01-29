---
name: football-match-trend-docs
description: Detailed documentation for the Football Match Trend Detail API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Match Trend Detail API Documentation

## Endpoint: Match Trends (Detail)
**URL:** `GET /v1/football/match/trend/detail`

This endpoint returns historical trend data (momentum/pressure) for completed matches.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | The Match ID. |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP-like status code (e.g., 200).
- **results** (array): List of trend objects.

#### Trend Object Fields (`results[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `match_id` | string | Unique Match ID. |
| `trend` | object | Trend data wrapper. |
| `trend.count` | integer | Number of halves/periods (usually 2). |
| `trend.per` | integer | Duration per half (e.g., 45 minutes). |
| `trend.data` | array | Array of arrays containing trend values. <br> Example: `[[FirstHalfData], [SecondHalfData]]`. <br> Inner array format: `[Minute, HomeValue, AwayValue]` or `[Minute, Value]`. <br> **Note:** Home team is positive, away team is negative. |

### Usage Recommendations
- **Request Limit:** Only available for matches within **30 days** before today.
- **Frequency:** 120 times/min (rate limit).
- **Fallback:** Use this interface to fill gaps if real-time trend data was missed.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/trend/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
