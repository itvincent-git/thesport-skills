---
name: football-deleted-data-docs
description: Detailed documentation for the Football Deleted Data API endpoint, including authentication, request parameters, and response field descriptions for synchronizing removals of matches, teams, players, and competitions.
---

# Football Deleted Data API Documentation

## Endpoint: Deleted Data
**URL:** `GET /v1/football/deleted`

This endpoint returns the IDs of data records (matches, teams, players, competitions, seasons, stages) that have been deleted within the last 24 hours. Regular synchronization is required to keep your local database clean.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `user` | string | Yes | Username. |
| `secret` | string | Yes | API Key. |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP status code.
- **results** (object): Wrapper for deleted IDs by category.

#### Result Fields (`results`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `match` | array | List of deleted Match IDs. |
| `team` | array | List of deleted Team IDs. |
| `player` | array | List of deleted Player IDs. |
| `competition` | array | List of deleted Competition IDs. |
| `season` | array | List of deleted Season IDs. |
| `stage` | array | List of deleted Stage IDs. |

### Usage Recommendations
- **Frequency:** Poll every **1 to 5 minutes**.
- **Window:** This endpoint only tracks deletions within the **last 24 hours**.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/deleted?user=YOUR_USER&secret=YOUR_SECRET"
```
