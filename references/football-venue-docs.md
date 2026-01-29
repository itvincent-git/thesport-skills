---
name: football-venue-docs
description: Detailed documentation for the Football Venue API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Venue API Documentation

## Endpoint: Venue List

**URL:** `GET /v1/football/venue/list`

This endpoint returns full venue (stadium) data. Supports both full and incremental updates based on time.

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
- **results** (array): List of venue objects.

#### Venue Object Fields (`results[]`)

| Field        | Type    | Description                                 |
|:------------ |:------- |:------------------------------------------- |
| `id`         | string  | Unique Venue ID.                            |
| `name`       | string  | Name of the venue.                          |
| `capacity`   | integer | Seating capacity.                           |
| `country_id` | string  | ID of the country/region.                   |
| `city`       | string  | City where the venue is located.            |
| `country`    | string  | Country name.                               |
| `uid`        | string  | Merged/Canonical ID if this is a duplicate. |
| `updated_at` | integer | Unix timestamp of the last update.          |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/venue/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/venue/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
