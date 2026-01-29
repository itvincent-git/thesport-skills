---
name: football-odds-history-docs
description: Documentation for the Football Single Match Odds API endpoint, providing full historical odds data for a specific match (initial, instant, and rolling).
---

# Football Single Match Odds API Documentation

## Endpoint: Single match odds

**URL:** `GET /v1/football/odds/history`

Return the full odd change data of a single match. Used to supplement real-time odds gaps.
Limit: Matches within 30 days before today.

### Request Parameters

| Name   | Type   | Description             |
|:------ |:------ |:----------------------- |
| `uuid` | string | **Required**. Match ID. |

### Response Structure

Structure is identical to **Real-time odds**, but organized by Company ID -> Odds Type -> History List.
