---
name: football-fifa-ranking-docs
description: Documentation for the FIFA Men's and Women's Ranking API endpoints, including points, ranking changes, and regional confederations.
---

# FIFA Ranking API Documentation

## Endpoints

- **Men:** `GET /v1/football/ranking/fifa/men`
- **Women:** `GET /v1/football/ranking/fifa/women`

### Request Parameters

| Name       | Type    | Description                                     |
|:---------- |:------- |:----------------------------------------------- |
| `pub_time` | integer | Release timestamp. Default is the latest issue. |

### Response Structure

| Field       | Type  | Description                                |
|:----------- |:----- |:------------------------------------------ |
| `pub_times` | array | List of all historical release timestamps. |
| `items[]`   | array | The ranking list for the requested issue.  |

#### Ranking Item Fields (`items[]`)

| Field              | Type    | Description                                                |
|:------------------ |:------- |:---------------------------------------------------------- |
| `team`             | object  | Team details (`id`, `name`, `logo`, `country_logo`).       |
| `region_id`        | integer | 1: UEFA, 2: CONMEBOL, 3: CONCACAF, 4: CAF, 5: AFC, 6: OFC. |
| `ranking`          | integer | Current rank.                                              |
| `points`           | integer | Current points.                                            |
| `position_changed` | integer | Change in rank from previous issue.                        |
