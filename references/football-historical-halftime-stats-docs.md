---
name: football-historical-halftime-stats-docs
description: Detailed documentation for the Football Team Half-time Statistics (Historical) API endpoint, including authentication, request parameters, and response field descriptions for period-specific metrics in completed matches.
---

# Football Historical Half-time Statistics API Documentation

## Endpoint: Team Half-time Statistics (Historical)

**URL:** `GET /v1/football/match/half/team_stats/detail`

This endpoint returns team-level statistics broken down by match periods (first half, second half, overtime) for completed matches.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type   | Required | Description   |
|:------ |:------ |:-------- |:------------- |
| `uuid` | string | Yes      | The Match ID. |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (object): Period-specific statistics object.

#### Period Object Fields (`results.Sign`)

*The field structure is identical to the **Match Team Half-time Statistics** endpoint.*

Key metrics:

- `ft`: Full Time.
- `p1`: First Half.
- `p2`: Second Half.
- `o1`: Overtime 1st Half.
- `o2`: Overtime 2nd Half.

Each period contains **Statistics IDs** mapping to `[HomeValue, AwayValue]`.

*For detailed ID mapping, refer to `football-halftime-team-stats-docs.md`.*

### Usage Recommendations

- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/half/team_stats/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
