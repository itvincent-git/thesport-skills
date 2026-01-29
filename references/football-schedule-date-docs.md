---
name: football-schedule-date-docs
description: Detailed documentation for the Football Schedule (Date Query) API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Schedule (Date Query) API Documentation

## Endpoint: Schedule and Results (Date Query)

**URL:** `GET /v1/football/match/diary`

This endpoint returns match data for a specific date or within 24 hours of a timestamp.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type    | Required | Description                                                                  |
|:------ |:------- |:-------- |:---------------------------------------------------------------------------- |
| `date` | string  | Yes*     | Query date in `YYYYMMDD` format (e.g., `20230101`). Returns full day's data. |
| `tsp`  | integer | Yes*     | Unix timestamp. Returns data within 24 hours after this timestamp.           |

*Note: Use either `date` OR `tsp`.*

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP-like status code (e.g., 200).
- **query** (object): Metadata about the request.
- **results** (array): List of match objects (same structure as Match List).
- **results_extra** (object): Linked data (Competition, Team, Referee, Venue, Season, Stage) to reduce redundancy.

#### Match Object Fields (`results[]`)

*See `football-match-recent-docs.md` for the full Match Object definition. The structure is identical.*

### Example Request

**By Date:**

```bash
curl "https://api.thesports.com/v1/football/match/diary?user=YOUR_USER&secret=YOUR_SECRET&date=20230101"
```

**By Timestamp:**

```bash
curl "https://api.thesports.com/v1/football/match/diary?user=YOUR_USER&secret=YOUR_SECRET&tsp=1672531200"
```
