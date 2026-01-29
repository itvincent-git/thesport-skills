---
name: football-coach-docs
description: Detailed documentation for the Football Coach API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Coach API Documentation

## Endpoint: Coach List

**URL:** `GET /v1/football/coach/list`

This endpoint returns coach data. Supports both full and incremental updates based on time.

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
- **results** (array): List of coach objects.

#### Coach Object Fields (`results[]`)

| Field                 | Type    | Description                                 |
|:--------------------- |:------- |:------------------------------------------- |
| `id`                  | string  | Unique Coach ID.                            |
| `team_id`             | string  | ID of the current team.                     |
| `name`                | string  | Full name of the coach.                     |
| `short_name`          | string  | Abbreviated name.                           |
| `logo`                | string  | URL string for the coach logo.              |
| `type`                | integer | `1`: Head Coach, `2`: Interim Head Coach.   |
| `age`                 | integer | Age of the coach.                           |
| `birthday`            | integer | Timestamp of birth.                         |
| `country_id`          | string  | ID of the country/region.                   |
| `nationality`         | string  | Nationality string.                         |
| `preferred_formation` | string  | Preferred tactical formation.               |
| `joined`              | integer | Timestamp of joining current team.          |
| `contract_until`      | integer | Timestamp of contract expiration.           |
| `uid`                 | string  | Merged/Canonical ID if this is a duplicate. |
| `deathday`            | integer | Timestamp of death (if applicable).         |
| `updated_at`          | integer | Unix timestamp of the last update.          |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/coach/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/coach/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
