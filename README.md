# hmz-n8n-workflows

> **8,159 production-ready n8n automation workflows** — the largest curated n8n library for agency, marketing, and AI automation use cases.

Part of the [HMZ AI System](https://github.com/hmzainjamil/claude-ai-system).

---

## Scale

| Metric | Count |
|---|---|
| Total workflows | 8,159 |
| Gmail / Email automations | 874 |
| Telegram bot workflows | 309 |
| Slack automations | 328 |
| Social media flows | 197 |
| CRM / Lead gen flows | 121 |
| Shopify / E-commerce | 82 |

## Top Categories

### 📧 Gmail / Email (874 workflows)
Cold outreach sequences, inbox automation, email → Airtable pipelines, bounce handling, reply detection, Mailchimp sync.

### 💬 Slack (328 workflows)
Alert routing, standup bots, lead notification, Claude Code → Slack bridges, channel management.

### 🤖 AI / GPT / LLM (varied)
OpenAI API integrations, Claude pipelines, prompt chaining, RAG workflows, AI content generators.

### 📊 Google Sheets (varied)
Lead imports, ad reporting sync, KPI dashboards, scheduled data pulls, formula automation.

### 📱 Social Media (197 workflows)
Instagram scheduling, Twitter/X auto-post, LinkedIn content, TikTok caption generation.

## How to Use

```bash
# Search by keyword
grep -i "shopify" ~/installed-repos/n8nworkflows.xyz/workflow_index.txt

# Browse by category
ls ~/installed-repos/n8nworkflows.xyz/workflows/ | grep -i "gmail"

# Load in n8n
# Import any .json file via n8n UI → Settings → Import Workflow
```

## Integration with HMZ Stack

Workflows auto-suggested by `optimize-commands` skill based on task keywords:
- Say "send cold email" → suggested Gmail/SMTP workflows
- Say "notify slack" → suggested Slack workflows
- Say "sync leads to crm" → suggested Apollo/HubSpot workflows

---

**Owner:** [Hafiz Muhammad Zulqarnain](https://github.com/hmzainjamil) — SEM/PPC Specialist & AI Automation Engineer  
**Main repo:** [claude-ai-system](https://github.com/hmzainjamil/claude-ai-system)
