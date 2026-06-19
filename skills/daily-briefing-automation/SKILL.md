---
name: daily-briefing-automation
version: 1.0.0
description: A comprehensive skill that generates personalized daily briefings by aggregating weather, news, portfolio updates, tasks, and calendar events into one actionable digest.
activation:
  keywords:
    - daily briefing
    - morning briefing
    - daily digest
    - weather forecast
    - portfolio update
    - news digest
    - calendar summary
    - daily tasks
    - morning report
  patterns:
    - "generate daily briefing"
    - "what's the weather"
    - "show portfolio performance"
    - "top news today"
    - "tasks for today"
    - "calendar events today"
    - "configure briefing"
    - "schedule daily briefing"
  tags:
    - automation
    - daily-digest
    - weather
    - portfolio
    - news
    - tasks
    - calendar
    - productivity
  max_context_tokens: 8000
---

# Daily Briefing Automation

A comprehensive skill that generates personalized daily briefings by aggregating weather, news, portfolio updates, tasks, and calendar events into one actionable digest.

## Problem Solved
Users waste 30+ minutes every morning checking multiple apps for critical information. This skill consolidates everything into one automated briefing delivered to your preferred channel.

## Features
- **Weather Forecasts**: Current conditions and 7-day outlook
- **Portfolio Tracking**: Daily performance updates and alerts
- **News Digest**: Curated headlines by topic
- **Task Overview**: Priority tasks for today
- **Calendar Summary**: Today's events and reminders
- **Automated Delivery**: Scheduled daily delivery via Telegram/Slack

## Commands
- `generate`: Create a full daily briefing
- `weather`: Get weather forecast for your location
- `portfolio`: Show portfolio performance summary
- `news`: Fetch top news headlines by topic
- `tasks`: List priority tasks for today
- `calendar`: Show today's calendar events
- `configure`: Set briefing preferences
- `schedule`: Configure automated delivery

## Installation
1. Place this SKILL.md in your skill directory
2. Run: `ironclaw skill install daily-briefing-automation`
3. Configure settings in `config/settings.json`
4. Run: `ironclaw skill run daily-briefing-automation generate`

## Dependencies
- `http`: For weather and news APIs
- `web_search`: For curated news
- `message`: For delivering briefings
