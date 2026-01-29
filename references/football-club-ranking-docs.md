---
name: football-club-ranking-docs
description: Documentation for the World Club Ranking API endpoint, providing global club standings based on points and ranking progress.
---

# World Club Ranking API Documentation

## Endpoint: World Clubs Ranking

**URL:** `GET /v1/football/ranking/club`

### Response Structure

#### Ranking Fields (`results[]`)

| Field              | Type    | Description                          |
|:------------------ |:------- |:------------------------------------ |
| `team`             | object  | Club details (`id`, `name`, `logo`). |
| `ranking`          | integer | Global rank.                         |
| `points`           | integer | Points.                              |
| `position_changed` | integer | Rank change.                         |
