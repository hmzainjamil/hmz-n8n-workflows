# hmz-n8n-workflows
> 8,159 production-ready n8n workflow JSONs — indexed, searchable, importable. Covers 300+ integrations.

[![workflows](https://img.shields.io/badge/workflows-8159-blue?style=flat&labelColor=555)](workflows/)
[![integrations](https://img.shields.io/badge/integrations-300+-green?style=flat&labelColor=555)](index/)
[![n8n](https://img.shields.io/badge/n8n-self--hosted-orange?style=flat&labelColor=555)](https://n8n.io)
[![indexed](https://img.shields.io/badge/index-searchable-purple?style=flat&labelColor=555)](workflow_index.txt)
[![license](https://img.shields.io/badge/license-MIT-lightgrey?style=flat&labelColor=555)](LICENSE)

[concepts](#concepts) · [architecture](#architecture) · [tips](#tips) · [startups](#startups) · [star](#star)

---

## 🧠 CONCEPTS <a id="concepts"></a>

| Feature | Location | Description |
|---|---|---|
| [**Workflow Index**](workflow_index.txt) | `workflow_index.txt` | Searchable flat-file index of all 8,159 workflows by name + tags |
| [**Gmail Workflows**](workflows/gmail/) | `workflows/gmail/` | 874 email automation flows — sequences, triggers, auto-reply, CRM sync |
| [**Slack Workflows**](workflows/slack/) | `workflows/slack/` | 328 Slack automations — alerts, standup, digest, notifications |
| [**Lead Gen Flows**](workflows/leads/) | `workflows/leads/` | 121 lead flows — Apollo, Hunter, LinkedIn, email enrichment |
| [**Social Workflows**](workflows/social/) | `workflows/social/` | 197 social flows — Instagram, Twitter, LinkedIn auto-post |
| [**Telegram Flows**](workflows/telegram/) | `workflows/telegram/` | 309 Telegram bot workflows — commands, alerts, webhooks |
| [**Shopify Flows**](workflows/ecommerce/) | `workflows/ecommerce/` | 82 e-commerce flows — orders, inventory, abandoned cart |
| [**Airtable / Notion**](workflows/database/) | `workflows/database/` | Sync, CRUD, webhook triggers for Airtable and Notion |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [**AI Agent Flows**](workflows/ai-agents/) | `workflows/ai-agents/` | Webhook → LLM → action chains using Claude/GPT/Groq nodes |
| [**Apollo to Mailchimp**](workflows/leads/apollo-mailchimp.json) | `workflows/leads/` | Full lead gen pipeline: Apollo search → enrich → Mailchimp CSV |
| [**Meta Ads Reporter**](workflows/ads/meta-ads-report.json) | `workflows/ads/` | Pulls Meta Ads metrics → Google Sheets → email daily |

---

## ⚙️ ARCHITECTURE <a id="architecture"></a>

```
User searches workflow_index.txt
          │
    grep -i "topic" workflow_index.txt
          │
    Found: workflows/category/name.json
          │
    Import to n8n (self-hosted or cloud)
          │
    Customize credentials + webhook URLs
          │
    Activate workflow → runs on trigger
```

| Category | Count | Top integration |
|---|---|---|
| Email (Gmail) | 874 | Gmail → CRM → Slack |
| Telegram bots | 309 | Webhook → LLM → Telegram |
| Slack automation | 328 | Trigger → filter → Slack |
| Lead gen | 121 | Apollo → enrich → email |
| Social media | 197 | Schedule → generate → post |
| E-commerce | 82 | Shopify orders → fulfillment |

---

## 💡 TIPS AND TRICKS (12) <a id="tips"></a>

[search](#tips-search) · [import](#tips-import) · [ai-flows](#tips-ai)

<a id="tips-search"></a>
■ **Searching (4)**

| Tip | Source |
|---|---|
| `grep -i "apollo" ~/installed-repos/n8nworkflows.xyz/workflow_index.txt` — instant search | [hmzainjamil](https://github.com/hmzainjamil) |
| Index format: `filename|tags|description|node_count` — filter by node count for complexity | [hmzainjamil](https://github.com/hmzainjamil) |
| `grep -c ""` on a category folder tells you how many workflows in that niche | [hmzainjamil](https://github.com/hmzainjamil) |
| MAE auto-suggests workflows: "write code" in optimize-commands activates n8n search | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-import"></a>
■ **Importing (4)**

| Tip | Source |
|---|---|
| n8n import: Settings → Import Workflow → paste JSON content | [n8n docs](https://docs.n8n.io/workflows/import-export/) |
| Always update credentials node after import — workflow keeps template creds as placeholder | [n8n](https://n8n.io) |
| Self-hosted n8n via Docker: `docker run -p 5678:5678 n8nio/n8n` — local instance ready in 30s | [n8n](https://docs.n8n.io/hosting/) |
| Use n8n CLI: `n8n import:workflow --input=workflow.json` for bulk import | [n8n CLI](https://docs.n8n.io/hosting/cli-commands/) |

<a id="tips-ai"></a>
■ **AI Flows (4)**

| Tip | Source |
|---|---|
| AI Agent node in n8n uses OpenAI-compatible API — point to Ollama localhost for free inference | [n8n AI nodes](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/) |
| Chain: Webhook trigger → Groq LLM → Slack notification — fastest AI pipeline in n8n | [hmzainjamil](https://github.com/hmzainjamil) |
| Use HTTP Request node with Bytez API for 100+ free models in any n8n workflow | [Bytez](https://bytez.com) |
| Store LLM outputs in Airtable via Airtable node — builds searchable knowledge base | [Airtable](https://airtable.com) |

---

## ☠️ STARTUPS / BUSINESSES <a id="startups"></a>

| Feature | Replaced |
|---|---|
| **8,159 workflow templates** | [Zapier Templates](https://zapier.com/templates), [Make.com templates](https://make.com/templates) |
| **Self-hosted automation** | [Zapier](https://zapier.com), [Make.com](https://make.com), [Pipedream](https://pipedream.com) |
| **AI agent workflows** | [Relevance AI](https://relevanceai.com), [Voiceflow](https://voiceflow.com) |
| **Lead gen automation** | [Apollo sequences](https://apollo.io), [Outreach.io](https://outreach.io), [Salesloft](https://salesloft.com) |

---

## Star History <a id="star"></a>

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-n8n-workflows&type=Date)](https://star-history.com/#hmzainjamil/hmz-n8n-workflows&Date)
