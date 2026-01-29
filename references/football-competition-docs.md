---
name: football-competition-docs
description: Detailed documentation for the Football Competition API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Competition API Documentation

## Endpoint: Competition List

**URL:** `GET /v1/football/competition/additional/list`

This endpoint returns full competition data (leagues, cups, friendlies) and supports both full and incremental updates.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type    | Required | Description                                                                                                                      |
|:------ |:------- |:-------- |:-------------------------------------------------------------------------------------------------------------------------------- |
| `page` | integer | No       | Page number (starts at 1). Default is 1000 records per page. Use for full updates by incrementing until no results are returned. |
| `time` | integer | No       | Unix timestamp. Returns records updated at or after this time. Use for incremental updates (recommended frequency: 1 min).       |
| `uuid` | string  | No       | Filter by a specific unique identifier.                                                                                          |

### Response Structure

The response is a JSON object containing the status code, query metadata, and the list of results.

#### Top-Level Fields

- **code** (integer): HTTP-like status code (e.g., 200).
- **query** (object): Metadata about the request execution.
  - `total` (integer): Total count of data available.
  - `type` (string): Query type used (uuid, page, or time).
  - `page` (integer): Current page number (if page query).
  - `time` (integer): Timestamp used (if time query).
  - `min_time` (integer): Smallest `updated_at` in the result set.
  - `max_time` (integer): Largest `updated_at` in the result set.
- **results** (array): List of competition objects.

#### Competition Object Fields (`results[]`)

| Field             | Type    | Description                                                           |
|:----------------- |:------- |:--------------------------------------------------------------------- |
| `id`              | string  | Unique Competition ID.                                                |
| `category_id`     | string  | ID of the category this competition belongs to.                       |
| `country_id`      | string  | ID of the country/region.                                             |
| `name`            | string  | Full name of the competition.                                         |
| `short_name`      | string  | Abbreviated name.                                                     |
| `logo`            | string  | URL string for the competition logo.                                  |
| `type`            | integer | `0`: Unknown, `1`: League, `2`: Cup, `3`: Friendly.                   |
| `cur_season_id`   | string  | ID of the current active season.                                      |
| `cur_stage_id`    | string  | ID of the current active stage.                                       |
| `cur_round`       | integer | Current round number.                                                 |
| `round_count`     | integer | Total number of rounds.                                               |
| `title_holder`    | array   | Defending champion info: `[TeamID (string), TitleCount (int)]`.       |
| `most_titles`     | array   | Most successful team: `[[TeamID (string)], TitleCount (int)]`.        |
| `newcomers`       | array   | Promotion/Relegation info: `[[PromotedTeamIDs], [RelegatedTeamIDs]]`. |
| `divisions`       | array   | Hierarchy info: `[[HigherLevelCompID], [LowerLevelCompID]]`.          |
| `host`            | object  | Hosting details: `{ "country": string, "city": string }`.             |
| `gender`          | integer | `1`: Male, `2`: Female.                                               |
| `primary_color`   | string  | Primary branding color (hex or name).                                 |
| `secondary_color` | string  | Secondary branding color.                                             |
| `uid`             | string  | Merged/Canonical ID if this is a duplicate.                           |
| `updated_at`      | integer | Unix timestamp of the last update.                                    |

### Example Request

**Full Sync (Page 1):**

```bash
curl "https://api.thesports.com/v1/football/competition/additional/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update (Since Timestamp):**

```bash
curl "https://api.thesports.com/v1/football/competition/additional/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```