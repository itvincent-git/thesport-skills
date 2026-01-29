---
name: football-schedule-season-docs
description: Detailed documentation for the Football Schedule (Season Query - Newest) API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Schedule (Season Query - Newest) API Documentation

## Endpoint: Schedule and Results (Season Query)
**URL:** `GET /v1/football/match/season/recent`

This endpoint returns the full schedule and results for a specific season. **Restriction:** It is typically used for the *newest* season.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | The Season ID to query. |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP-like status code (e.g., 200).
- **query** (object): Metadata about the request.
- **results** (array): List of match objects (same structure as Match List).
- **results_extra** (object): Linked data (Competition, Team, Referee, Venue, Season, Stage) to reduce redundancy.

#### Match Object Fields (`results[]`)
*See `football-match-recent-docs.md` for the full Match Object definition. The structure is identical.*

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/season/recent?user=YOUR_USER&secret=YOUR_SECRET&uuid=SEASON_ID"
```
