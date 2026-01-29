---
name: football-referee-docs
description: Detailed documentation for the Football Referee API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Referee API Documentation

## Endpoint: Referee List

**URL:** `GET /v1/football/referee/list`

This endpoint returns full referee data. Supports both full and incremental updates based on time.

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
- **results** (array): List of referee objects.

#### Referee Object Fields (`results[]`)

| Field        | Type    | Description                                 |
|:------------ |:------- |:------------------------------------------- |
| `id`         | string  | Unique Referee ID.                          |
| `name`       | string  | Full name of the referee.                   |
| `short_name` | string  | Abbreviated name.                           |
| `logo`       | string  | URL string for the referee logo.            |
| `birthday`   | integer | Timestamp of birth.                         |
| `country_id` | string  | ID of the country/region.                   |
| `uid`        | string  | Merged/Canonical ID if this is a duplicate. |
| `updated_at` | integer | Unix timestamp of the last update.          |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/referee/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/referee/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
