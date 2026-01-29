---
name: football-team-docs
description: Detailed documentation for the Football Team API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Team API Documentation

## Endpoint: Team List

**URL:** `GET /v1/football/team/additional/list`

This endpoint returns full team data and supports both full and incremental updates based on time.

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
- **query** (object): Metadata about the request (total, page, time, etc.).
- **results** (array): List of team objects.

#### Team Object Fields (`results[]`)

| Field                   | Type    | Description                                      |
|:----------------------- |:------- |:------------------------------------------------ |
| `id`                    | string  | Unique Team ID.                                  |
| `competition_id`        | string  | ID of the primary league the team belongs to.    |
| `country_id`            | string  | ID of the country/region.                        |
| `name`                  | string  | Full name of the team.                           |
| `short_name`            | string  | Abbreviated name.                                |
| `logo`                  | string  | URL string for the team logo.                    |
| `national`              | integer | `1`: National Team, `0`: Club Team.              |
| `country_logo`          | string  | Logo of the country (if national team).          |
| `foundation_time`       | integer | Year/Timestamp of foundation.                    |
| `website`               | string  | Official website URL.                            |
| `coach_id`              | string  | ID of the current coach.                         |
| `venue_id`              | string  | ID of the home venue.                            |
| `market_value`          | integer | Total market value of the team.                  |
| `market_value_currency` | string  | Currency of the market value.                    |
| `total_players`         | integer | Total number of players (-1 if no data).         |
| `foreign_players`       | integer | Number of foreign players (-1 if no data).       |
| `national_players`      | integer | Number of national team players (-1 if no data). |
| `uid`                   | string  | Merged/Canonical ID if this is a duplicate.      |
| `virtual`               | integer | `1`: Placeholder team, `0`: Real team.           |
| `gender`                | integer | `1`: Male, `2`: Female.                          |
| `updated_at`            | integer | Unix timestamp of the last update.               |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/team/additional/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/team/additional/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
