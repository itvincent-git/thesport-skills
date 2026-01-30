# Thesport Data Skill

This repository contains the **Thesport Data Skill** for the Gemini CLI. It provides an interface for the AI agent to access comprehensive documentation, endpoints, and data structures for **TheSports Football API**.

## Overview

This skill empowers the Gemini CLI to understand and retrieve information related to football (soccer) data, including competitions, matches, players, teams, odds, and statistics. It serves as a knowledge base for the API's capabilities.

## Features

The skill maps to various API endpoints and documentation located in the `references/` directory, categorized as follows:

### Basic Data

* **Competitions & Seasons:** Details on leagues, cups, stages, and seasons.
* **Entities:** Teams, Players, Coaches, Referees, and Venues.
* **Metadata:** Countries, Categories, and Languages.

### Match Data

* **Schedules & Results:** Historical and future match lists, season fixtures.
* **Real-time Info:** Live scores, trends, and match incidents (including GIFs).
* **Details:** Lineups, H2H analysis, TV channels, and venue coordinates.

### Statistics & Standings

* **Rankings:** FIFA rankings, Club rankings, and League Standings (Real-time & Season).
* **Performance:** Detailed match stats for Teams and Players.
* **Leaders:** Top scorers lists.

### Team & Player Intelligence

* **Squads:** Current team squads and injury reports.
* **Market:** Player transfers and market values.
* **History:** Honors and awards for players, teams, and coaches.

### Odds & Analysis

* **Betting:** Real-time and historical odds data.
* **Trends:** Match trends and compensation history.

## Repository Structure

* `SKILL.md`: The core definition file for the Gemini CLI skill. It maps user intents to the specific documentation files.
* `references/`: Contains individual Markdown files documenting specific parts of TheSports API (e.g., `football-player-docs.md`, `football-match-live-docs.md`).

## Installation

1. **Clone the repository:**
   
   ```bash
   git clone https://github.com/itvincent-git/thesport-skills/
   cd thesport-skills
   ```

2. **Add the skill to Gemini CLI:**
   Run the following command in your terminal to register the skill.
   
   ```bash
   gemini skill add ./SKILL.md
   ```

## Usage

Once the skill is installed and active, you can ask the agent questions such as:

* "What is the API endpoint for getting the Premier League standing?"
* "Show me the data structure for a player transfer."
* "How do I fetch live match odds?"
* "Explain the response format for match lineups."