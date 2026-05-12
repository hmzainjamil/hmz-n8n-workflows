# hmz-n8n-workflows

![Version](https://img.shields.io/badge/version-2.0-blue?style=flat&labelColor=555) ![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=555) ![License](https://img.shields.io/badge/license-MIT-orange?style=flat&labelColor=555) ![Models](https://img.shields.io/badge/models-Tier0-purple?style=flat&labelColor=555)

> 8,159 n8n workflow JSONs — email, Slack, CRM, Shopify, social, AI, data, telegram, lead gen, and more. Full MAE bridge integration for AI-driven automation.

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---|---|---|
| [Workflow Library](workflows/) | `workflows/` | 8,159 n8n JSON workflows — every business automation category covered |
| [Workflow Index](workflow_index.txt) | `workflow_index.txt` | Full-text searchable index of all 8,159 workflows — grep to find any flow |
| [Email Flows](workflows/email/) | `workflows/email/` | 874 Gmail/email automation workflows — sequences, drip, replies, parsing |
| [Slack Flows](workflows/slack/) | `workflows/slack/` | 328 Slack notification, bot, and channel management workflows |
| [Lead Gen Flows](workflows/leads/) | `workflows/leads/` | 121 lead generation flows — Apollo, Hunter, LinkedIn, email verification |
| [Social Flows](workflows/social/) | `workflows/social/` | 197 Instagram/Twitter/LinkedIn/TikTok content automation workflows |
| [Shopify Flows](workflows/shopify/) | `workflows/shopify/` | 82 Shopify/WooCommerce order, inventory, and customer workflows |
| [Telegram Flows](workflows/telegram/) | `workflows/telegram/` | 309 Telegram bot, notification, and automation workflows |
| [CRM Flows](workflows/crm/) | `workflows/crm/` | HubSpot, Salesforce, Pipedrive, Airtable sync and automation |
| [Data Flows](workflows/data/) | `workflows/data/` | Google Sheets, Notion, Airtable, NocoDB data pipeline workflows |
| [AI Flows](workflows/ai/) | `workflows/ai/` | OpenAI, Anthropic, Groq, Gemini AI-powered automation workflows |
| [Webhook Triggers](workflows/webhooks/) | `workflows/webhooks/` | Inbound webhook handler templates for any external system |
| [Scheduled Flows](workflows/scheduled/) | `workflows/scheduled/` | Cron-based daily/weekly/monthly report and data sync workflows |
| [MAE Bridge](bin/mae-n8n.sh) | `bin/mae-n8n.sh` | Triggers n8n workflows from MAE agent swarm — two-way integration |
| [Workflow Deployer](bin/deploy.sh) | `bin/deploy.sh` | Deploy any workflow JSON to n8n via API — one command |
| [Workflow Exporter](bin/export.sh) | `bin/export.sh` | Export all active n8n workflows to JSON for version control |
| [Error Handler](workflows/error-handler.json) | `workflows/error-handler.json` | Universal error workflow — Slack alert + retry on any failure |
| [Credential Manager](bin/creds.sh) | `bin/creds.sh` | Manage n8n credentials via CLI — create, list, delete |
| [Execution Monitor](bin/monitor.sh) | `bin/monitor.sh` | Monitor n8n execution log — alert on failures, track success rate |
| [Sub-workflow Pattern](workflows/patterns/sub-workflow.json) | `workflows/patterns/sub-workflow.json` | Reusable sub-workflow template — called from parent flows |
| [Queue Mode Config](config/queue.yml) | `config/queue.yml` | n8n queue mode with Redis — handles 1000s of concurrent executions |
| [Webhook Auth](config/webhook-auth.json) | `config/webhook-auth.json` | HMAC signature verification for all inbound webhooks |
| [Rate Limiter](workflows/rate-limiter.json) | `workflows/rate-limiter.json` | Built-in rate limiting for API calls — prevents hitting quotas |
| [Data Transform](workflows/transforms/) | `workflows/transforms/` | JSON, CSV, XML data transformation utility workflows |
| [Version Control](.gitignore) | `.gitignore` | Track workflow JSONs in git — full change history |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [8159 Workflow Library](workflow_index.txt) | `workflow_index.txt` | Every automation already built — grep index before writing any new flow |
| [MAE Bridge](bin/mae-n8n.sh) | `bin/mae-n8n.sh` | MAE agent swarm triggers n8n workflows — AI + automation combined |
| [Queue Mode](config/queue.yml) | `config/queue.yml` | Redis-backed queue handles unlimited concurrent workflow executions |
| [Universal Error Handler](workflows/error-handler.json) | `workflows/error-handler.json` | Single error workflow catches all failures → Slack alert + auto-retry |
| [One-Command Deployer](bin/deploy.sh) | `bin/deploy.sh` | Deploy any workflow JSON to n8n instantly via REST API |

---

## ⚙️ ARCHITECTURE

```
┌──────────────────────────────────────────────────────────────┐
│                  HMZ-N8N-WORKFLOWS v2.0                      │
│                                                              │
│  Trigger → n8n Workflow → Node chain → Output/Action        │
│                                                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ Webhook  │  │ Schedule │  │  Manual  │  │   MAE    │   │
│  │ triggers │  │   cron   │  │  click   │  │  bridge  │   │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘   │
│       └─────────────┴─────────────┴──────────────┘         │
│                           │                                  │
│              ┌────────────▼────────────┐                    │
│              │    n8n WORKFLOW ENGINE  │                    │
│              │  8,159 flows available  │                    │
│              │  Queue mode + Redis     │                    │
│              └────────────┬────────────┘                    │
│                           │                                  │
│   Email · Slack · CRM · Shopify · Social · AI · Data       │
└──────────────────────────────────────────────────────────────┘
```

| Layer | Technology | Volume |
|---|---|---|
| Workflow engine | n8n self-hosted | 8,159 workflows |
| Queue backend | Redis | Unlimited concurrency |
| Trigger types | Webhook / Cron / Manual / MAE | All covered |
| Integrations | 400+ n8n nodes | Every SaaS tool |

---

## 🚀 Quick Start

```bash
# Search workflow library
grep -i 'shopify order' workflow_index.txt

# Deploy a workflow
bash bin/deploy.sh workflows/shopify/order-fulfillment.json

# Export all active workflows
bash bin/export.sh --output exports/$(date +%Y%m%d)/

# Monitor executions
bash bin/monitor.sh --last 100 --failed-only

# Trigger from MAE
mae run "send weekly sales report via Slack"
```

---

## 💡 TIPS AND TRICKS (48)

<a id="tips-workflow-discovery-(6)"></a>
### ■ **Workflow Discovery (6) (6)**
| Tip | Source |
|---|---|
| grep -i 'keyword' workflow_index.txt — find any flow in 8,159 library instantly | [workflow_index.txt](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Sort results by recency — most recently updated flows are most reliable | [workflow_index.txt](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Search by integration name: 'hubspot', 'shopify', 'notion' — exact match | [workflow_index.txt](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Filter by trigger type: 'webhook', 'schedule', 'manual' in workflow name | [n8n](https://n8n.io) |
| Check README in each workflow folder — usage notes and credential requirements | [n8n](https://n8n.io) |
| Test workflow in n8n manually before adding webhook trigger in production | [n8n](https://n8n.io) |

<a id="tips-node-best-practices-(6)"></a>
### ■ **Node Best Practices (6) (6)**
| Tip | Source |
|---|---|
| Error branch on every HTTP Request node — never let 429s kill your flow | [n8n](https://n8n.io) |
| Set Item Batching on Code node — avoid OOM on 10K+ item datasets | [n8n](https://n8n.io) |
| Use Set node to clean data between steps — easier debugging | [n8n](https://n8n.io) |
| Function node vs Code node: Code node has full JS, use it for complex logic | [n8n](https://n8n.io) |
| Merge node modes: Append, Merge By Key, Multiplex — pick correct mode | [n8n](https://n8n.io) |
| Wait node: add delay between API calls — prevents rate limit hits | [n8n](https://n8n.io) |

<a id="tips-queue-&-scale-(6)"></a>
### ■ **Queue & Scale (6) (6)**
| Tip | Source |
|---|---|
| Queue mode with Redis: EXECUTIONS_MODE=queue — handles 1000+ concurrent runs | [n8n](https://n8n.io) |
| Scale workers: N8N_CONCURRENCY_PRODUCTION_LIMIT=10 per worker instance | [n8n](https://n8n.io) |
| Redis Streams mode for high-throughput — 10x faster than default queue | [Redis](https://redis.io) |
| Webhook load balancer: multiple n8n instances behind nginx — true HA | [nginx](https://nginx.org) |
| Use execution pruning: EXECUTIONS_DATA_MAX_AGE=168 (7 days) — saves disk | [n8n](https://n8n.io) |
| Monitor with n8n built-in execution log — grep failed runs by workflow ID | [n8n](https://n8n.io) |

<a id="tips-credentials-(6)"></a>
### ■ **Credentials (6) (6)**
| Tip | Source |
|---|---|
| Store all API keys as n8n credentials — never hardcode in workflow nodes | [n8n](https://n8n.io) |
| Use credential env vars: N8N_ENCRYPTION_KEY in .env — encrypts at rest | [n8n](https://n8n.io) |
| Share credentials across workflows — one update fixes all dependent flows | [n8n](https://n8n.io) |
| OAuth credential auto-refresh — n8n handles token refresh automatically | [n8n](https://n8n.io) |
| Test credentials before deploying — n8n credential test button | [n8n](https://n8n.io) |
| Export credentials backup: n8n export:credentials — add to encrypted vault | [n8n](https://n8n.io) |

<a id="tips-mae-integration-(6)"></a>
### ■ **MAE Integration (6) (6)**
| Tip | Source |
|---|---|
| mae-n8n.sh bridge triggers any workflow from MAE agent task | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| MAE decomposes goal → sub-tasks → n8n handles execution-heavy steps | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| Two-way: n8n webhook can trigger MAE run for AI-enhanced steps | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| Use n8n Execute Workflow node to chain from AI output to automation | [n8n](https://n8n.io) |
| mae daily uses n8n flows for data sync and Slack reporting steps | [mae daily](https://github.com/hmzainjamil/claude-ai-system) |
| All n8n outputs auto-pushed to Paperclip via webhook → company memory | [Paperclip](https://paperclip.ai) |

<a id="tips-error-handling-(6)"></a>
### ■ **Error Handling (6) (6)**
| Tip | Source |
|---|---|
| Universal error workflow catches all failures — one setup covers everything | [n8n](https://n8n.io) |
| Error workflow → Slack alert with: workflow name, node, error message, timestamp | [n8n](https://n8n.io) |
| Use IF node to check response status before continuing execution | [n8n](https://n8n.io) |
| Retry on failure: HTTP Request node has built-in retry with exponential backoff | [n8n](https://n8n.io) |
| Dead letter queue: failed executions → Airtable log for manual review | [n8n](https://n8n.io) |
| Test error flow: manually throw error in Code node — verify alert fires | [n8n](https://n8n.io) |

<a id="tips-performance-(6)"></a>
### ■ **Performance (6) (6)**
| Tip | Source |
|---|---|
| Disable unnecessary logging in production: N8N_LOG_LEVEL=warn | [n8n](https://n8n.io) |
| Use database for execution history: N8N_EXECUTION_DATA_SAVE_ON_SUCCESS=none | [n8n](https://n8n.io) |
| Batch HTTP calls: merge 10 webhook payloads → one API call with array | [n8n](https://n8n.io) |
| Cache frequent lookups: Redis SET/GET in Code node — avoid repeat API calls | [Redis](https://redis.io) |
| Split In Batches node: 50 items/batch for Shopify API — avoids 429s | [n8n](https://n8n.io) |
| Profile slow workflows: execution time in n8n log — optimize bottleneck node | [n8n](https://n8n.io) |

<a id="tips-deployment-(6)"></a>
### ■ **Deployment (6) (6)**
| Tip | Source |
|---|---|
| Version control: git commit all workflow JSONs — full change history | [git](https://git-scm.com) |
| bin/deploy.sh: curl POST to n8n API — one command deploys any workflow | [deploy.sh](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| bin/export.sh: export all active flows to JSON before any n8n upgrade | [export.sh](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Docker deploy: docker-compose.yml with n8n + Redis + Postgres — production-ready | [Docker](https://docker.com) |
| Environment variables in .env — never hardcode n8n config in docker-compose | [Docker](https://docker.com) |
| Health check endpoint: /healthz — use in load balancer or uptime monitor | [n8n](https://n8n.io) |


---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|---|---|
| 8,159 automation workflows | [Zapier Templates](https://zapier.com/templates) |
| Queue mode infinite scale | [Make.com](https://make.com) |
| Universal error handler | [PagerDuty](https://pagerduty.com) |
| MAE + n8n AI-automation bridge | [Activepieces](https://activepieces.com) |
| Workflow version control | [GitHub Actions](https://github.com/features/actions) |
| One-command workflow deploy | [Retool](https://retool.com) |
| Redis queue backend | [Bull/BullMQ](https://bullmq.io) |
| Credential encryption | [Vault by HashiCorp](https://vaultproject.io) |
| Execution monitoring | [Datadog](https://datadoghq.com) |
| Webhook auth layer | [Svix](https://svix.com) |
| Data transformation | [Airbyte](https://airbyte.com) |
| Sub-workflow pattern | [AWS Step Functions](https://aws.amazon.com/step-functions/) |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-n8n-workflows&type=Date)](https://star-history.com/#hmzainjamil/hmz-n8n-workflows&Date)
