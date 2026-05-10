# hmz-n8n-workflows — 8,159 n8n Workflow JSON Files

> **The largest personal n8n workflow library. 8,159 automation templates across every business function.**

---

## Overview

`hmz-n8n-workflows` is a curated collection of 8,159 n8n workflow JSON files organized by business function. It represents years of community-built automation templates, hand-selected and organized for agency operations.

These workflows power the HMZ agency's backend automation layer: from BDM outreach to client reporting, lead nurturing to social media scheduling. Every workflow is importable directly into any n8n instance.

**Total workflows: 8,159**
**Total categories: 25+**
**Ready to import: Yes (JSON format)**

---

## Workflow Categories & Counts

| Category | Count | Primary Use |
|----------|-------|------------|
| Gmail / Email | 874 | Cold outreach, follow-ups, notifications |
| Slack | 328 | Team alerts, client updates, notifications |
| Telegram | 309 | Personal automation, bot messaging |
| AI / LLM | 400+ | GPT, Claude, Gemini integrations |
| CRM / Sales | 121 | Pipeline management, deal tracking |
| LinkedIn | 80+ | Profile scraping, connection automation |
| Google Sheets | 200+ | Data sync, reporting, dashboards |
| Airtable | 150+ | Database operations, CRM records |
| Social Media | 197 | Posting, scheduling, engagement |
| E-commerce | 82 | Orders, inventory, customer data |
| SEO / Content | 100+ | Keyword research, content generation |
| Data / Reporting | 200+ | Analytics, dashboards, exports |
| Webhook | 300+ | API integrations, event triggers |
| Database | 150+ | MySQL, PostgreSQL, MongoDB |
| Google Workspace | 250+ | Docs, Sheets, Calendar, Drive |
| HubSpot | 75 | CRM sync, deal automation |
| Salesforce | 45 | Enterprise CRM workflows |
| Stripe | 60 | Payment processing, invoicing |
| Notion | 90+ | Knowledge base, project management |
| Discord | 65 | Community management, alerts |
| Twitter/X | 80 | Social automation (read-only) |
| YouTube | 40 | Content tracking, analytics |
| Calendly | 35 | Meeting scheduling, CRM sync |
| Typeform | 45 | Form processing, lead capture |
| Other/Misc | 1,000+ | Custom integrations, utilities |

---

## Key Workflow Bundles

### 1. BDM (Business Development) Pipeline

The most critical bundle for HMZ operations. Automates the entire business development cycle.

**Workflows included:**
- `linkedin-job-search-auto-apply.json` — Searches LinkedIn for matching jobs
- `indeed-job-scraper.json` — Scrapes Indeed job posts matching HMZ criteria
- `lead-qualifier-score.json` — Scores leads against criteria (budget, fit, timeline)
- `cover-letter-ai-generator.json` — Generates tailored cover letters via GPT-4o-mini
- `application-tracker-airtable.json` — Logs all applications to Airtable
- `follow-up-sequence-gmail.json` — 3-touch follow-up sequence after application
- `meeting-book-calendly.json` — Auto-books discovery calls when leads respond

**Trigger:** New job post matching keywords → full pipeline runs automatically

```
LinkedIn/Indeed Job Post
    |
    v
Filter: Keywords + Budget + Location
    |
    v
Qualify: HMZ scoring rubric
    |
    v (if score >= 70)
Generate: Cover letter (GPT-4o-mini)
    |
    v
Send: Gmail application
    |
    v
Log: Airtable record
    |
    v
Schedule: Follow-up sequence (Day 3, Day 7, Day 14)
```

### 2. Lead Nurture Sequences

Email sequences for warming prospects who haven't responded.

**Workflows:**
- `nurture-cold-day1.json` — Initial value-add email
- `nurture-cold-day3.json` — Case study / social proof
- `nurture-cold-day7.json` — Direct ask / offer
- `nurture-cold-day14.json` — Final breakup email
- `nurture-warm-retargeting.json` — For prospects who opened but didn't respond
- `nurture-reengagement.json` — For dormant leads (30+ days)

### 3. Weekly Client Reporting

Automated weekly performance reports for all active clients.

**Workflows:**
- `google-ads-weekly-pull.json` — Pulls metrics from Google Ads API
- `meta-ads-weekly-pull.json` — Pulls Facebook/Instagram ad metrics
- `ga4-weekly-traffic.json` — Pulls website analytics
- `report-compiler.json` — Merges all data into a report template
- `report-pdf-generator.json` — Generates branded PDF via ReportLab
- `report-send-client.json` — Emails report to client with Gmail
- `report-log-sheets.json` — Logs metrics to Google Sheets dashboard

**Schedule:** Every Monday 8AM → full report delivered to client inbox by 9AM

### 4. AI/LLM Integration Workflows (400+)

The largest AI automation collection in the library.

**Subcategories:**
- **OpenAI workflows (150+):** GPT-4, GPT-3.5, DALL-E, Whisper integrations
- **Claude workflows (80+):** Anthropic API, Claude Code triggers
- **Gemini workflows (60+):** Google AI Studio, Vertex AI
- **Ollama workflows (40+):** Local LLM automation
- **Multi-model workflows (70+):** Routing across providers

**Highlight workflows:**
- `ai-email-responder.json` — AI reads incoming emails and drafts responses
- `ai-content-repurposer.json` — Converts blog posts to 5 social formats
- `ai-ad-copy-generator.json` — Generates 10 ad variants per prompt
- `ai-competitor-monitor.json` — Monitors competitor websites, summarizes changes
- `ai-lead-scoring.json` — Scores inbound leads via LLM analysis
- `ai-proposal-drafter.json` — Auto-drafts client proposals from intake form

### 5. Social Media Automation (197 Workflows)

**Platforms covered:**
- LinkedIn (posting, engagement — read-only compliant)
- Twitter/X (posting via API)
- Instagram (via Facebook Graph API)
- YouTube (upload notifications, analytics)
- Discord (community management)

**Key workflows:**
- `linkedin-post-scheduler.json` — Posts LinkedIn content on schedule
- `content-repurpose-multi-platform.json` — One piece → 5 platforms
- `social-engagement-monitor.json` — Tracks mentions and comments
- `reddit-post-throttle.json` — Posts to Reddit with mandatory delay (max 1/day to avoid ban detection)

### 6. Google Workspace Integration (250+ Workflows)

- **Sheets:** Data sync, formula automation, dashboard updates
- **Docs:** Auto-generate documents from templates
- **Drive:** File organization, sharing permissions
- **Calendar:** Meeting scheduling, reminder sequences
- **Gmail:** Email parsing, auto-labeling, draft generation

---

## Directory Structure

```
hmz-n8n-workflows/
  email/
    gmail/
      cold-outreach/     (50+ workflows)
      follow-up/         (40+ workflows)
      notifications/     (30+ workflows)
    smtp/                (20+ workflows)
  
  crm/
    hubspot/             (75 workflows)
    salesforce/          (45 workflows)
    airtable/            (150+ workflows)
    pipedrive/           (30 workflows)
  
  ai-llm/
    openai/              (150+ workflows)
    anthropic/           (80+ workflows)
    google-gemini/       (60+ workflows)
    ollama/              (40+ workflows)
    multi-model/         (70+ workflows)
  
  social/
    linkedin/            (80+ workflows)
    twitter/             (80 workflows)
    instagram/           (40 workflows)
    discord/             (65 workflows)
  
  reporting/
    google-ads/          (40 workflows)
    meta-ads/            (35 workflows)
    analytics/           (50+ workflows)
    pdf-export/          (30 workflows)
  
  productivity/
    google-workspace/    (250+ workflows)
    notion/              (90+ workflows)
    slack/               (328 workflows)
    telegram/            (309 workflows)
  
  ecommerce/
    shopify/             (40 workflows)
    stripe/              (60 workflows)
    woocommerce/         (25 workflows)
  
  data/
    database/            (150+ workflows)
    webhooks/            (300+ workflows)
    transformations/     (100+ workflows)
```

---

## How to Import Workflows

### Method 1: n8n UI

1. Open n8n (http://localhost:5678)
2. Click "Workflows" in sidebar
3. Click "Import" button
4. Select any `.json` file from this repo

### Method 2: n8n CLI

```bash
# Import a single workflow
n8n import:workflow --input=./email/gmail/cold-outreach/cold-email-v3.json

# Import all workflows in a directory
for f in ./email/gmail/*.json; do
  n8n import:workflow --input="$f"
done
```

### Method 3: API Import

```bash
curl -X POST http://localhost:5678/api/v1/workflows \
  -H "X-N8N-API-KEY: your_key" \
  -H "Content-Type: application/json" \
  -d @workflow.json
```

---

## n8n Setup for HMZ Stack

### Installation

```bash
# Docker (recommended)
docker run -d \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n

# npm
npm install n8n -g
n8n start
```

### Required Credentials

Configure these in n8n Settings > Credentials:

| Service | Credential Type |
|---------|----------------|
| Gmail | OAuth2 |
| Google Ads | OAuth2 |
| Meta/Facebook | OAuth2 |
| Airtable | API Key |
| Slack | OAuth2 |
| OpenAI | API Key |
| Anthropic | API Key |
| Google Gemini | API Key |
| HubSpot | API Key / OAuth2 |
| LinkedIn | OAuth2 |

### Always-On Setup (LaunchAgent)

```xml
<!-- ~/Library/LaunchAgents/com.hmz.n8n.plist -->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "...">
<plist version="1.0">
<dict>
  <key>Label</key><string>com.hmz.n8n</string>
  <key>ProgramArguments</key>
  <array><string>n8n</string><string>start</string></array>
  <key>KeepAlive</key><true/>
  <key>RunAtLoad</key><true/>
</dict>
</plist>
```

---

## Top 20 Most-Used Workflows in HMZ

| # | Workflow | Daily Runs |
|---|---------|-----------|
| 1 | weekly-client-report-compiler | 7 (weekly) |
| 2 | linkedin-job-monitor | 3x daily |
| 3 | gmail-cold-outreach-v5 | 2x daily |
| 4 | google-ads-alerts | 4x daily |
| 5 | meta-ads-spend-monitor | 4x daily |
| 6 | airtable-lead-sync | Continuous |
| 7 | ai-email-draft | On trigger |
| 8 | slack-daily-digest | 1x daily |
| 9 | ga4-traffic-alert | 4x daily |
| 10 | content-repurposer | 2x daily |

---

## License

Workflows are community-sourced from n8n's template library and custom-built for HMZ operations. Free to use under community sharing principles.

---

*8,159 workflows. Every business function automated. Built for a one-person agency that operates like a team of 50.*
