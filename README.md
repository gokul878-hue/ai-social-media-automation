# AI-Powered Social Media Content Automation

An event-driven **n8n + Google Gemini** workflow that turns an article link into platform-specific social media content for LinkedIn, X, and Instagram.

## Overview

The workflow starts when a new article link is added to Google Sheets. Google Gemini summarizes the article, then separate AI chains adapt that summary for different social platforms.

### Current implementation

- Google Sheets trigger for incoming article links
- Gemini-powered article summarization
- Separate content-generation chains for:
  - LinkedIn
  - X (Twitter)
  - Instagram
- Automated publishing node currently connected for **LinkedIn**
- X and Instagram content is generated, but direct publishing nodes are not yet connected in the current workflow

## Architecture

```text
Google Sheets
     |
     v
Gemini Article Summary
     |
     +----------------+----------------+
     |                |                |
     v                v                v
 LinkedIn             X           Instagram
 Generator        Generator        Generator
     |
     v
LinkedIn Publish
```

## Tech Stack

| Component | Technology |
|---|---|
| Workflow automation | n8n |
| LLM | Google Gemini |
| Trigger source | Google Sheets |
| Social publishing | LinkedIn node/API |
| Workflow format | JSON |

## Why use separate AI chains?

Each social platform has different expectations for tone, structure, length, and audience. Dedicated prompts make the generated content more platform-appropriate than reusing one generic post everywhere.

## Repository Structure

```text
ai-social-media-automation/
├── README.md
├── screenshot.png
└── workflow.json
```

## Setup

1. Install or open an n8n instance.
2. Import `workflow.json`.
3. Connect your own Google Sheets and Google Gemini credentials.
4. Replace the placeholder Google Sheet ID with your sheet ID.
5. Configure LinkedIn credentials if you want automatic LinkedIn publishing.
6. Add and configure X/Instagram publishing nodes if you want direct publishing to those platforms.
7. Activate the workflow.

> Credentials and secrets are intentionally not stored in this repository.

## Workflow Logic

1. A new Google Sheets row provides an article link.
2. Gemini generates a concise article summary with key insights and audience implications.
3. The summary branches into three separate prompt chains.
4. Each chain generates content adapted to its target platform.
5. LinkedIn content is passed to the configured LinkedIn publishing node.

## Future Improvements

- Add direct X publishing
- Add direct Instagram publishing
- Add approval-before-publish mode
- Store generated posts back in Google Sheets
- Add error handling and retry logic
- Add scheduling and analytics

## Skills Demonstrated

- Event-driven workflow design
- LLM prompt engineering
- API-based automation
- Multi-platform content adaptation
- n8n workflow orchestration

---

Built as a personal project to explore AI automation, LLM-based content transformation, and social-media workflow orchestration.
