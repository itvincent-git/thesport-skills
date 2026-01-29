---
name: football-country-docs
description: Detailed documentation for the Football Country/Region API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Country/Region API Documentation

## Endpoint: Country/Region List

**URL:** `GET /v1/football/country/list`

This endpoint returns a list of all countries and regions available in the football database. This data rarely changes.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name     | Type   | Required | Description                        |
|:-------- |:------ |:-------- |:---------------------------------- |
| `user`   | string | Yes      | Username, please contact business. |
| `secret` | string | Yes      | Key, please contact business.      |

*Note: This endpoint does not currently support page or time-based incremental queries in the documentation, as the data is static and small enough to be returned in a single call.*

### Response Structure

The response is a JSON object containing a status code and the list of results.

#### Top-Level Fields

- **code** (integer): HTTP-like status code (e.g., 200).
- **results** (array): List of country/region objects.

#### Country/Region Object Fields (`results[]`)

| Field         | Type    | Description                                                                     |
|:------------- |:------- |:------------------------------------------------------------------------------- |
| `id`          | string  | Unique Country/Region ID.                                                       |
| `category_id` | string  | ID of the category this country belongs to (e.g., a continent or region group). |
| `name`        | string  | Full name of the country or region.                                             |
| `logo`        | string  | URL string for the country/region logo (often a flag).                          |
| `updated_at`  | integer | Unix timestamp of the last update.                                              |

### Example Request

**Fetch All Countries:**

```bash
curl "https://api.thesports.com/v1/football/country/list?user=YOUR_USER&secret=YOUR_SECRET"
```

### Usage Recommendations

- **Request Frequency:** Data rarely changes; recommended frequency is **1 day/time**.
- **Caching:** Highly recommended to cache this data locally.
