# hmz-n8n-workflows
8,159 n8n workflow templates + custom DigiMinds automation workflows — visual pipeline builder for integrating APIs, webhooks, and AI models without code.

![workflows](https://img.shields.io/badge/templates-8159-blue?style=flat&labelColor=555) ![custom](https://img.shields.io/badge/custom_workflows-15%2B-green?style=flat&labelColor=555) ![integrations](https://img.shields.io/badge/integrations-400%2B-orange?style=flat&labelColor=555) ![company](https://img.shields.io/badge/DigiMinds-agency-red?style=flat&labelColor=555)

[Concepts](#-concepts) · [Hot](#-hot) · [Inventory](#️-workflow-inventory) · [Tips](#-tips-and-tricks-20) · [Replaced](#️-startups--businesses) · [Stars](#star-history)

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**8,159 Templates**](~/installed-repos/n8nworkflows.xyz/workflows/) | `~/installed-repos/n8nworkflows.xyz/` | Full community template library — searchable locally, import directly to n8n instance |
| [**Custom Workflows**](workflows/) | `workflows/` | DigiMinds-specific: lead routing, content publishing, KPI alerts, client reporting, audit delivery |
| [**AI Node**](workflows/ai-nodes/) | `workflows/ai-nodes/` | Connects to Ollama, Groq, Gemini, OpenAI directly inside n8n — no code needed |
| [**Webhook Triggers**](workflows/webhooks/) | `workflows/webhooks/` | Paperclip API events → n8n webhook → multi-step automation |
| [**Composio Integration**](workflows/composio/) | `workflows/composio/` | n8n calls Composio HTTP nodes for 200+ tool connections |
| [**Credential Store**](https://n8n.io/docs/credentials/) | n8n UI | OAuth tokens for all services stored in n8n credential vault — never in workflow JSON |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**n8n AI Agent node**](workflows/ai-nodes/) | `workflows/ai-nodes/` | Native agent loop inside n8n — chain tool calls without code |
| [**Sub-workflow pattern**](workflows/) | `workflows/` | Complex workflows split into reusable sub-workflows — called like functions |
| [**Error workflow**](workflows/error-handler.json) | `workflows/error-handler.json` | Global error handler catches all failures — logs to Paperclip API + Slack alert |

---

## ⚙️ WORKFLOW INVENTORY

| Workflow | Trigger | Integrations | Output |
|----------|---------|--------------|--------|
| Lead Qualification Router | Webhook (Paperclip) | Apollo + HubSpot + Slack | Lead in CRM + Slack alert |
| LinkedIn Content Publisher | Daily 10 AM | LinkedIn API + Gemini | Scheduled post |
| Client Audit Delivery | Manual trigger | Gmail + Google Drive + Stripe | Audit PDF emailed + invoiced |
| KPI Alert Router | Webhook (KPI monitor) | Slack + Gmail + Paperclip | Alert to HMZ |
| Cold Email Sequence | Apollo webhook | Apollo + Mailgun + HubSpot | 5-step email sequence |
| Competitor Intel Digest | Mon/Wed/Fri | Apify + Slack + Paperclip | Intel brief in Slack |
| Onboarding Automation | New client in HubSpot | Notion + Slack + Gmail | Welcome kit + workspace |
| Invoice Automation | Project complete | Stripe + QuickBooks + Gmail | Auto-invoice sent |
| Google Ads Alert | GA4 threshold breach | Google Ads API + Slack | ROAS drop alert |
| Meta Ads Alert | Meta webhook | Meta API + Slack + Paperclip | CPM spike alert |

---

## 💡 TIPS AND TRICKS (20)

[Design](#tips-design) · [AI nodes](#tips-ai) · [Triggers](#tips-trig) · [Error](#tips-err) · [Templates](#tips-tmpl)

<a id="tips-design"></a>■ **Workflow Design (6)**

| Tip | Source |
|-----|--------|
| Every workflow must have an error trigger — connect to global error handler | [n8n best practice](https://n8n.io/docs) |
| Split complex workflows into sub-workflows — max 20 nodes per flow | [Maintainability rule](workflows/) |
| Use Set node to normalize data between integrations — schema drift kills workflows | [Data hygiene](workflows/) |
| Always test with real data, not dummy data — n8n test mode hides integration issues | [Testing rule](workflows/) |
| Use `$workflow.id` + timestamp as idempotency key for external API calls | [Design pattern](workflows/) |
| Retry on failure: set node retry count to 3 with exponential backoff | [Reliability](https://n8n.io/docs) |

<a id="tips-ai"></a>■ **AI Nodes (4)**

| Tip | Source |
|-----|--------|
| Point n8n AI node to Ollama (`http://localhost:11434/v1`) for free local inference | [Tier 0](../hmz-ollama/) |
| Use Groq credential in n8n for fastest cloud inference in time-sensitive workflows | [Groq](../hmz-g0dm0d3/) |
| AI Agent node in n8n chains tool calls — use for multi-step research workflows | [n8n docs](https://n8n.io/docs) |
| Gemini Flash = best n8n AI node default — 1,500 free/day, strong quality | [Cost rule](../hmz-g0dm0d3/) |

<a id="tips-trig"></a>■ **Triggers (4)**

| Tip | Source |
|-----|--------|
| Webhook triggers from Paperclip API → n8n are more reliable than cron triggers | [Architecture](../hmz-digiminds-ceo/) |
| Use `Schedule Trigger` not cron for n8n — survives n8n restarts, cron doesn't | [n8n docs](https://n8n.io/docs) |
| Deduplicate webhook events with a cache node — Paperclip may send duplicate events | [Reliability](workflows/) |
| Test webhooks locally with ngrok or n8n's built-in webhook test URL | [Dev workflow](https://n8n.io/docs) |

<a id="tips-err"></a>■ **Error Handling (3)**

| Tip | Source |
|-----|--------|
| Global error workflow: connect all workflows' "On Error" to one handler | [n8n pattern](workflows/error-handler.json) |
| Error handler logs to Paperclip API + sends Slack alert — both, always | [Ops rule](workflows/) |
| Never use `Continue on Error` without logging — silent failures are invisible | [Debug rule](workflows/) |

<a id="tips-tmpl"></a>■ **Templates (3)**

| Tip | Source |
|-----|--------|
| `find ~/installed-repos/n8nworkflows.xyz -name "*.json" \| xargs grep "slack"` to find templates | [Local search](~/installed-repos/n8nworkflows.xyz/) |
| Import template: n8n UI → Workflows → Import from file | [n8n UI](https://n8n.io) |
| Community templates at [n8n.io/workflows](https://n8n.io/workflows) — 8K+ and growing | [Community](https://n8n.io) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **Visual workflow builder** | [Zapier](https://zapier.com), [Make](https://make.com) — expensive per-task pricing, vendor lock-in |
| **AI nodes (local + cloud)** | Separate AI integrations in each automation platform |
| **8,159 template library** | Starting from scratch for every new workflow |
| **Self-hosted n8n** | [Zapier](https://zapier.com) $19-99/mo · [Make](https://make.com) $9-29/mo per workspace |
| **Webhook triggers** | Polling cron jobs — delayed reactions, unnecessary API calls |
| **Sub-workflow pattern** | Duplicating logic across multiple workflows |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-n8n-workflows&type=Date)](https://star-history.com/#hmzainjamil/hmz-n8n-workflows&Date)