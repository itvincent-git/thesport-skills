---
name: football-match-tv-docs
description: Documentation for the Match TV Channels API endpoint, listing broadcasting channels for football matches by country.
---

# Match TV Channels API Documentation

## Endpoint: Match TV Channels

**URL:** `GET /v1/football/match/tv/list`

### Response Structure

#### TV Item Fields (`results[].tv[]`)

| Field        | Type   | Description                                               |
|:------------ |:------ |:--------------------------------------------------------- |
| `country_id` | string | Country ID.                                               |
| `names`      | array  | List of channel names (e.g., ["Sky Sports", "BT Sport"]). |
