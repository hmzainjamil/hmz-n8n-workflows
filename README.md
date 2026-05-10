# hmz-n8n-workflows

> **8,159 n8n automation workflows** — the complete HMZ workflow library organized by integration, ready to import and run.

Part of [claude-ai-system](https://github.com/hmzainjamil/claude-ai-system).

---

## Overview

The largest curated n8n workflow collection in the HMZ stack. Every workflow is a JSON file importable into any n8n instance in one click.

```
~/installed-repos/n8nworkflows.xyz/workflows/    ← 8,159 JSON files
~/installed-repos/n8nworkflows.xyz/workflow_index.txt  ← searchable index
```

---

## Workflow Categories

| Category | Count | Top Use Cases |
|---|---|---|
| Gmail/Email | ~874 | Cold outreach, follow-up sequences, inbox zero |
| Slack | ~328 | Lead alerts, team updates, status notifications |
| Telegram | ~309 | Bot responses, lead capture, CRM updates |
| AI/GPT/LLM | ~400+ | Content gen, lead scoring, research, summarization |
| CRM/Sales | ~121 | Apollo, HubSpot, Salesforce, Pipedrive sync |
| LinkedIn | ~80+ | Profile scraping, connection automation |
| Google Sheets | ~200+ | KPI reporting, data pipeline, live dashboards |
| Airtable | ~150+ | CRM, lead management, project tracking |
| Social Media | ~197 | Instagram, Twitter, Facebook, TikTok posting |
| Ecommerce | ~82 | Shopify, WooCommerce, Stripe, order automation |
| SEO/Content | ~100+ | Blog auto-post, keyword research, content scheduling |
| Data/Reporting | ~200+ | Dashboards, analytics pipelines, KPI flows |
| Security | ~50+ | Compliance checks, access audit, alerting |
| Other | ~3,000+ | Webhooks, databases, APIs, custom integrations |

---

## HMZ Active Workflows

### Daily BDM Sweep
```
LinkedIn Search → filter by title/company/budget signals
→ Apollo enrich → Airtable CRM
→ Personalized cold email + PDF audit
→ Follow-up sequence (Day 1/3/7/14)
```

### Indeed Pipeline
```
Indeed MCP search → filter ($15+/hr, 90+ score, <48hr)
→ Claude generates cover letter
→ Application submitted → tracking Airtable
```

### Cold Email Outreach
```
Prospect list (Airtable) → research (Apify)
→ Claude writes personalized email + unique PDF
→ Gmail send → tracking → follow-up
```

### Reporting Automation
```
Google Ads API → Google Sheets
→ Claude generates insights
→ PDF report → email to client
→ Slack notification to team
```

---

## How to Find Workflows

```bash
# Search by keyword
grep -i "linkedin" ~/installed-repos/n8nworkflows.xyz/workflow_index.txt

# Search by integration
grep -i "apollo" ~/installed-repos/n8nworkflows.xyz/workflow_index.txt | head -20

# Browse by category
ls ~/installed-repos/n8nworkflows.xyz/workflows/ | grep -i "gmail" | head -20
```

---

## Import to n8n

1. Open your n8n instance
2. Click **+New** → **Import from file**
3. Select any `.json` from the workflows folder
4. Configure credentials → Activate

---

## Self-Host n8n

```bash
# Docker (recommended)
docker run -it --rm   --name n8n   -p 5678:5678   -v ~/.n8n:/home/node/.n8n   n8nio/n8n

# Visit: http://localhost:5678
```

---

## Full System

[claude-ai-system](https://github.com/hmzainjamil/claude-ai-system) | [claude-ai-workflows](https://github.com/hmzainjamil/claude-ai-workflows) | [hmz-installed-repos](https://github.com/hmzainjamil/hmz-installed-repos)

---

*HMZ AI Agency — 8,159 workflows auto-indexed daily*
