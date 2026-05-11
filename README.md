<p align="center">
  <img src="https://img.shields.io/badge/HMZ-N8N%20WORKFLOWS-F86606?style=for-the-badge&logoColor=white" alt="HMZ n8n Workflows" height="60">
</p>

<h1 align="center">HMZ n8n Workflows</h1>

<p align="center">
  <strong>8,159 production-ready n8n automation workflows — Gmail, Slack, CRM, Shopify, AI/LLM, and 50+ platforms</strong>
</p>

<p align="center">
  <a href="https://github.com/hmzainjamil"><img src="https://img.shields.io/badge/By-HMZ-6C3EE8?style=for-the-badge" alt="By HMZ"></a>
  <a href="#categories"><img src="https://img.shields.io/badge/Workflows-8%2C159-F86606?style=for-the-badge" alt="8159 Workflows"></a>
  <a href="#categories"><img src="https://img.shields.io/badge/Categories-14-20A34E?style=for-the-badge" alt="14 Categories"></a>
  <a href="#"><img src="https://img.shields.io/badge/n8n-Compatible-246DFF?style=for-the-badge" alt="n8n Compatible"></a>
  <a href="https://github.com/hmzainjamil/hmz-n8n-workflows/stargazers"><img src="https://img.shields.io/github/stars/hmzainjamil/hmz-n8n-workflows?style=for-the-badge&color=9D97F4&label=Stars" alt="Stars"></a>
</p>

<p align="center">
  <a href="#overview">Overview</a> &bull;
  <a href="#quick-start">Quick Start</a> &bull;
  <a href="#categories">Categories</a> &bull;
  <a href="#use-cases">Use Cases</a> &bull;
  <a href="#installation">Installation</a> &bull;
  <a href="#resources">Resources</a>
</p>

---

## Overview

**HMZ n8n Workflows** is a curated library of 8,159 production-ready n8n automation JSON files, organized by platform and use case. Import any workflow into your n8n instance — or ask Claude Code to find and adapt the right one for your use case.

What makes this library different:
- **8,159 workflows** — largest private n8n collection, covering virtually every automation use case
- **Claude Code searchable** — the full manifest is indexed; ask "find me a workflow for Gmail → Airtable lead capture" and Claude finds it in seconds
- **14 categories** — Gmail/Email, Slack, LinkedIn, CRM, Shopify, AI/LLM, Telegram, Google Sheets, and more
- **Production-tested** — workflows sourced from n8nworkflows.xyz, the largest community collection

---

## Quick Start

```bash
# Search for workflows via Claude Code
"Find me an n8n workflow for Gmail → Airtable lead capture"
"Find Shopify → Slack order notification workflow"
"Find n8n workflow for LinkedIn lead scraping → CRM"

# Search the manifest directly
grep -i "gmail" ~/installed-repos/n8nworkflows.xyz/workflow_index.txt | head -20
grep -i "shopify" ~/installed-repos/n8nworkflows.xyz/workflow_index.txt | head -20

# Import a workflow into n8n
# 1. Browse WORKFLOW-MANIFEST.md to find the workflow name
# 2. Find the JSON in ~/installed-repos/n8nworkflows.xyz/workflows/<name>/
# 3. Import via n8n UI: Settings → Import from File
```

---

## Categories

| Category | Count | Top platforms |
|---|---|---|
| **Gmail / Email** | 874 | Gmail, Mailchimp, SendGrid, Outlook, IMAP |
| **Slack** | 328 | Slack, Slack bots, Slack notifications |
| **CRM / Sales** | 298 | HubSpot, Salesforce, Apollo, Pipedrive, Close |
| **Telegram** | 309 | Telegram bots, Telegram notifications, Telegraf |
| **AI / GPT / LLM** | 421 | OpenAI, Claude, Gemini, LangChain, Pinecone, RAG |
| **Google Sheets** | 318 | Sheets sync, Sheets → CRM, Sheets reporting |
| **Social Media** | 197 | Instagram, Twitter/X, Facebook, TikTok, YouTube |
| **Ecommerce** | 82 | Shopify, WooCommerce, Stripe, PayPal |
| **LinkedIn** | 156 | LinkedIn scraping, lead gen, outreach automation |
| **Airtable** | 203 | Airtable sync, Airtable CRM, Airtable reporting |
| **Data / Reporting** | 287 | Google Analytics, Looker, BigQuery, data pipelines |
| **SEO / Content** | 144 | WordPress auto-post, SEO monitoring, content pipelines |
| **Security / Compliance** | 67 | Audit logs, access monitoring, compliance alerts |
| **Other** | 3,575 | Notion, Jira, GitHub, Zapier migration, Webhooks, etc. |

---

## Use Cases

| Goal | Example prompt | Workflow found |
|---|---|---|
| **Lead capture to CRM** | "Gmail → HubSpot contact create when email received from new domain" | `gmail-hubspot-lead-capture` |
| **Shopify order alerts** | "Shopify new order → Slack #sales channel notification with order value" | `shopify-slack-order-notification` |
| **LinkedIn lead scraping** | "LinkedIn search → extract profiles → add to Apollo → export CSV" | `linkedin-apollo-lead-pipeline` |
| **AI customer support** | "Intercom ticket → GPT-4 → classify + auto-reply → escalate to human if complex" | `intercom-gpt4-support-bot` |
| **Content auto-publishing** | "Google Sheets blog calendar → WordPress auto-publish on schedule" | `sheets-wordpress-auto-publish` |
| **Sales pipeline sync** | "Stripe payment → HubSpot deal close → Slack team notification → invoice email" | `stripe-hubspot-slack-invoice` |
| **Competitor monitoring** | "Daily: scrape competitor site → compare with yesterday → Slack diff alert" | `competitor-monitor-slack-alert` |
| **Invoice processing** | "Gmail attachment → extract invoice data via AI → add to Airtable → send approval" | `gmail-ai-invoice-airtable` |

---

## Installation

### Option 1: Clone the full library (recommended)

```bash
git clone https://github.com/hmzainjamil/hmz-n8n-workflows.git
# Browse WORKFLOW-MANIFEST.md to find workflows
# Import JSON files directly into n8n
```

### Option 2: Use via Claude Code

```bash
# Ask Claude to find and adapt any workflow:
"Find an n8n workflow for [your use case] and adapt it for [your specific setup]"
# Claude searches WORKFLOW-MANIFEST.md and returns the adapted JSON
```

### Option 3: Run n8n locally

```bash
# n8n runs as a LaunchAgent in HMZ system
launchctl load ~/Library/LaunchAgents/ai.hmz.n8n.plist
# Access at http://localhost:5678
```

---

## Prerequisites

1. **n8n instance** — self-hosted (`npx n8n`) or n8n.cloud
2. **n8n credentials** — configure your platform credentials in n8n Settings → Credentials
3. **Node.js 18+** — required for self-hosted n8n
4. **Relevant API keys** — each workflow requires credentials for its platforms (see workflow README)

---

## Resources

- **[n8n.io](https://n8n.io)** — n8n documentation and community
- **[n8nworkflows.xyz](https://n8nworkflows.xyz)** — source community for this workflow collection
- **[claude-ai-system](https://github.com/hmzainjamil/claude-ai-system)** — full HMZ system (these workflows are part of it)
- **[claude-ai-workflows](https://github.com/hmzainjamil/claude-ai-workflows)** — meta-workflows and pipeline documentation
- **[hmz-composio](https://github.com/hmzainjamil/hmz-composio)** — Composio MCP for 250+ app integrations

---

## Support

- [Open an issue](https://github.com/hmzainjamil/hmz-n8n-workflows/issues)
- [LinkedIn](https://linkedin.com/in/hmzainjamil)

## License

MIT

---

<p align="center">
  Built by <a href="https://github.com/hmzainjamil">Hafiz Muhammad Zulqarnain</a> &mdash; HMZ AI Agency
</p>

<p align="center">
  <sub>8,159 workflows. All searchable via Claude Code. Ask: "Find me an n8n workflow for [use case]"</sub>
</p>