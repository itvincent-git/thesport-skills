---
name: football-category-docs
description: Detailed documentation for the Football Category API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Category API Documentation

## Endpoint: Category List

**URL:** `GET /v1/football/category/list`

This endpoint returns a list of all football categories (typically continents or region groups). This data rarely changes.

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
- **results** (array): List of category objects.

#### Category Object Fields (`results[]`)

| Field        | Type    | Description                              |
|:------------ |:------- |:---------------------------------------- |
| `id`         | string  | Unique Category ID.                      |
| `name`       | string  | Category Name (e.g., "Europe", "World"). |
| `updated_at` | integer | Unix timestamp of the last update.       |

### Example Request

```bash
curl "https://api.thesports.com/v1/football/category/list?user=YOUR_USER&secret=YOUR_SECRET"
```

### Usage Recommendations

- **Request Frequency:** Data rarely changes; recommended frequency is **1 day/time**.
