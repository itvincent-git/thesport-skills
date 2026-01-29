---
name: football-odds-update-docs
description: Documentation for the Football Odds Update API endpoint, listing matches with odds updates in the last 60 seconds to guide selective syncing.
---

# Football Odds Update API Documentation

## Endpoint: Odds update

**URL:** `GET /v1/football/odds/update`

Returns the list of matches that had odds updates in the last 60 seconds. Use this to know which matches to query via "Single match odds" if real-time stream was missed.

### Response Structure

#### Result Fields (`results[]`)

| Field         | Type    | Description              |
|:------------- |:------- |:------------------------ |
| `id`          | string  | Match ID.                |
| `company_id`  | integer | Company ID with updates. |
| `update_time` | integer | Update timestamp.        |
