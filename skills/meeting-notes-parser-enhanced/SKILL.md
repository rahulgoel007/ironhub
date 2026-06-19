---
name: meeting-notes-parser-enhanced
version: 1.0.0
description: Transform unstructured meeting notes from Zoom, Google Meet, Teams, and Webex into structured action items with speaker diarization, real-time processing, and auto-post to Slack, Jira, Asana, Notion, and Email.
activation:
  keywords:
    - meeting notes
    - action items
    - meeting summary
    - transcript
    - meeting parser
    - zoom meeting
    - google meet
    - teams meeting
    - meeting transcription
    - action item extraction
  patterns:
    - "meeting.*notes"
    - "action.*item"
    - "meeting.*summary"
    - "transcript.*parse"
    - "zoom.*meeting"
    - "google.*meet"
    - "teams.*meeting"
  tags:
    - automation
    - meetings
    - productivity
    - transcription
    - platform-integration
  max_context_tokens: 8000
---

# Enhanced Universal Meeting Notes Parser

## Problem It Solves

After every meeting, someone has to manually read through messy, unstructured notes and figure out:
- Who is doing what?
- By when?
- What was decided?
- What were the key points discussed?

This skill automates this entirely by parsing raw meeting notes from Zoom, Google Meet, Teams, and Webex with speaker diarization, and auto-posting to Slack, Jira, Asana, Notion, and Email.

---

## Key Improvements Over Original Skill

| Feature | Original | Enhanced |
|---------|----------|----------|
| **Platforms** | Manual paste only | Zoom, Google Meet, Teams, Webex |
| **Speaker Tracking** | Manual "Owner: Name" | Auto diarization (AssemblyAI, Whisper) |
| **Real-time** | Post-meeting only | Live during call |
| **Auto-Post** | None | Slack, Jira, Asana, Notion, Email |
| **Calendar Sync** | None | Auto-read from Google Calendar |
| **Transcription** | None | Whisper, AssemblyAI, Google Speech, Azure |

---

## Output Formats

| Format | Use Case |
|--------|----------|
| **Plain Text** | Human-readable summary |
| **JSON** | API integrations, automation |
| **Slack Message** | Direct paste into Slack with emojis |
| **CSV** | Excel/Google Sheets ready |


---

## CLI Commands

```bash
# Parse meeting notes (text)
meeting-notes-parser --input notes.txt

# Parse meeting notes (JSON)
meeting-notes-parser --input notes.txt --format json

# Parse meeting notes (Slack)
meeting-notes-parser --input notes.txt --format slack

# Parse meeting notes (CSV)
meeting-notes-parser --input notes.txt --format csv

# Fetch from Zoom
meeting-notes-parser --source zoom --meeting-id abc123

# Fetch from Google Calendar (latest)
meeting-notes-parser --source google-calendar --latest

# Fetch from Google Meet
meeting-notes-parser --source google-meet --event-id xyz789

# Fetch from Microsoft Teams
meeting-notes-parser --source teams --meeting-id teams123

# Live mode during meeting
meeting-notes-parser --mode live --platform zoom --meeting-id abc123

# Auto-post to Slack
meeting-notes-parser --source zoom --meeting-id abc123 --post-to slack --channel "#standup"

# Create Jira tickets
meeting-notes-parser --source zoom --meeting-id abc123 --create-jira-tickets

# Export everywhere
meeting-notes-parser --source zoom --meeting-id abc123 --export json --export csv --export email

# Filter by priority
meeting-notes-parser --input notes.txt --priority high

# Filter by owner
meeting-notes-parser --input notes.txt --owner Priya

# Use specific transcription provider
meeting-notes-parser --source zoom --meeting-id abc123 --transcription assemblyai

# Use Whisper local fallback
meeting-notes-parser --source zoom --meeting-id abc123 --transcription whisper

---

## Architecture

meeting-notes-parser-enhanced/
├── src/
│   ├── __init__.py
│   ├── parser.py                    ← Core skill logic
│   ├── cli.py                       ← CLI interface
│   ├── integrations/
│   │   ├── __init__.py
│   │   ├── zoom.py                  ← Zoom API (meetings, recordings, transcripts)
│   │   ├── google_meet.py           ← Google Meet + Calendar
│   │   ├── microsoft_teams.py       ← Teams API
│   │   ├── webex.py                 ← Webex API
│   │   └── transcription.py         ← Multi-provider adapter
│   ├── exporters/
│   │   ├── __init__.py
│   │   ├── slack.py                 ← Slack webhook
│   │   ├── jira.py                  ← Jira tickets
│   │   ├── asana.py                 ← Asana tasks
│   │   ├── notion.py                ← Notion pages
│   │   └── email.py                 ← Gmail
│   └── realtime/
│       ├── __init__.py
│       ├── websocket_listener.py    ← Live transcription
│       └── speaker_diarizer.py      ← Speaker ID
├── tests/
│   ├── test_parser.py               ← Unit tests
│   └── test_integrations.py         ← Integration tests
├── examples/
│   ├── sample_notes.txt             ← Example input
│   ├── zoom_integration.py          ← Zoom usage demo
│   ├── google_calendar_integration.py
│   └── teams_integration.py
├── .github/workflows/
│   └── ci.yml                       ← GitHub Actions CI
├── SKILL.md                         ← This file
├── README.md
├── pyproject.toml
├── requirements.txt
└── LICENSE

---

## Environment Variables

# Zoom
ZOOM_CLIENT_ID=xxx
ZOOM_CLIENT_SECRET=xxx

# Google
GOOGLE_CLIENT_ID=xxx
GOOGLE_CLIENT_SECRET=xxx
GOOGLE_SERVICE_ACCOUNT=xxx

# Microsoft Teams
MICROSOFT_CLIENT_ID=xxx
MICROSOFT_CLIENT_SECRET=xxx

# Transcription
ASSEMBLYAI_API_KEY=xxx
WHISPER_MODEL=large-v3

# Auto-post
SLACK_WEBHOOK_URL=xxx
JIRA_API_TOKEN=xxx
ASANA_PERSONAL_ACCESS_TOKEN=xxx
NOTION_API_KEY=xxx
GMAIL_API_KEY=xxx
