# hmz-n8n-workflows
Production n8n workflow library — AI automation, lead gen, content, and agency operations.

![workflows](https://img.shields.io/badge/workflows-30%2B-blue?style=flat&labelColor=555)
![platform](https://img.shields.io/badge/platform-n8n-orange?style=flat&labelColor=555)
![tier0](https://img.shields.io/badge/models-Tier0_first-green?style=flat&labelColor=555)
![status](https://img.shields.io/badge/status-production-brightgreen?style=flat&labelColor=555)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat&labelColor=555)

[Concepts](#-concepts) · [Architecture](#️-architecture) · [Tips](#-tips-and-tricks-20) · [Kills](#️-startups--businesses) · [Stars](#star-history)

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**BDM Lead Sweep**](workflows/bdm-lead-sweep.json) | `workflows/bdm-lead-sweep.json` | Morning LinkedIn scrape → score → personalized outreach via GPT-4o-mini [![daily](https://img.shields.io/badge/schedule-08%3A00-blue?style=flat&labelColor=555)] |
| [**Reddit Poster**](workflows/reddit-poster.json) | `workflows/reddit-poster.json` | 1 post/day max (bot-watch compliance) — value-first, no agency links in body |
| [**Competitor Intel**](workflows/competitor-intel.json) | `workflows/competitor-intel.json` | Weekly scrape → pricing delta → Slack alert if competitor changes rates |
| [**LinkedIn Content**](workflows/linkedin-content.json) | `workflows/linkedin-content.json` | Sunday batch-generate week of posts — Gemini draft → human approval step |
| [**Audit PDF Trigger**](workflows/audit-pdf.json) | `workflows/audit-pdf.json` | Webhook → extract prospect URL → brand palette → ReportLab 11-page PDF |
| [**Email Sequence**](workflows/email-sequence.json) | `workflows/email-sequence.json` | Cold → follow-up → close — 5-email chain, Instantly/Smartlead compatible |
| [**KPI Alert**](workflows/kpi-alert.json) | `workflows/kpi-alert.json` | Hourly ROAS/CPL check → Slack DM if metric drops >15% |
| [**Skill Sync**](workflows/skill-sync.json) | `workflows/skill-sync.json` | GitHub webhook → pulls new SKILL.md → activates in Claude Code via API |
| [**Session Queue**](workflows/session-queue.json) | `workflows/session-queue.json` | Reads session-queue.jsonl → writes to persistent memory files |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**Paperclip Webhook**](workflows/paperclip-webhook.json) | `workflows/paperclip-webhook.json` | Receives CEO loop decisions → dispatches to correct n8n sub-workflow |
| [**Per-Prospect PDF**](workflows/per-prospect-pdf.json) | `workflows/per-prospect-pdf.json` | Each cold email gets unique PDF — business name, city, brand palette from URL |
| [**GitHub Portfolio Sync**](workflows/github-sync.json) | `workflows/github-sync.json` | 06:30 daily — mirrors local ~/.claude/bin to GitHub repos via Contents API |

## ⚙️ ARCHITECTURE

```
n8n Workflow Categories:

  BDM / Lead Gen
    ├─ bdm-lead-sweep (daily 08:00)
    ├─ email-sequence (triggered on new lead)
    └─ per-prospect-pdf (webhook)

  Content
    ├─ linkedin-content (Sunday batch)
    ├─ reddit-poster (daily, 1 max)
    └─ audit-pdf (on-demand webhook)

  Intel
    ├─ competitor-intel (weekly)
    └─ kpi-alert (hourly)

  Infrastructure
    ├─ skill-sync (GitHub webhook)
    ├─ session-queue (Stop hook)
    └─ github-sync (daily 06:30)
```

## 💡 TIPS AND TRICKS (20)

[n8n](#tips-n8n) · [ai-nodes](#tips-ai-nodes) · [webhooks](#tips-webhooks) · [scheduling](#tips-scheduling)

<a id="tips-n8n"></a>■ **n8n Fundamentals (5)**

| Tip | Source |
|-----|--------|
| Self-host n8n locally — no monthly cost, full control, runs via LaunchAgent | [n8n](https://n8n.io/self-hosted) |
| Export workflows as JSON — version control in this repo, restore on crash | [HMZ](https://github.com/hmzainjamil) |
| Use `Error Workflow` node — catches failures and logs to Slack channel | [HMZ](https://github.com/hmzainjamil) |
| n8n credentials: store API keys once in Settings → Credentials, reuse everywhere | [n8n Docs](https://docs.n8n.io/credentials) |
| `n8n start --tunnel` for webhook testing — exposes local n8n to internet temporarily | [n8n Docs](https://docs.n8n.io/hosting/configuration/configuration-examples/webhook-url) |

<a id="tips-ai-nodes"></a>■ **AI Nodes (5)**

| Tip | Source |
|-----|--------|
| Route n8n AI nodes to Groq/Gemini — never OpenAI for cost-sensitive workflows | [HMZ](https://github.com/hmzainjamil) |
| OpenRouter node: set model dynamically — switch to cheapest model per task type | [HMZ](https://github.com/hmzainjamil) |
| Use `Code` node for caveman compression — strip output before passing to next node | [HMZ](https://github.com/hmzainjamil) |
| Batch AI calls in a single node with array input — reduces API round-trips 5x | [HMZ](https://github.com/hmzainjamil) |
| Cache AI responses in n8n Variables — avoid re-calling for same input within session | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-webhooks"></a>■ **Webhooks (5)**

| Tip | Source |
|-----|--------|
| Use `Respond to Webhook` node immediately — don't block webhook caller during processing | [n8n Docs](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.respondtowebhook) |
| Validate webhook auth header — add `Header Auth` to all production webhooks | [HMZ](https://github.com/hmzainjamil) |
| GitHub webhook → n8n → skill-sync: fires on push to claude-ai-skills repo | [HMZ](https://github.com/hmzainjamil) |
| Store webhook URLs in n8n Variables — easy to update without editing each workflow | [HMZ](https://github.com/hmzainjamil) |
| Test webhooks with `n8n execute --id <workflow-id>` before enabling in production | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-scheduling"></a>■ **Scheduling (5)**

| Tip | Source |
|-----|--------|
| Stagger heavy workflows by 10+ minutes — avoid simultaneous API bursts | [HMZ](https://github.com/hmzainjamil) |
| Reddit: 1 post/day max — bot-watch account, never schedule 2-3/day | [HMZ](https://github.com/hmzainjamil) |
| LinkedIn content: batch Sunday, approve Monday — human review step before publish | [HMZ](https://github.com/hmzainjamil) |
| KPI check: hourly during business hours (08:00-22:00), skip overnight | [HMZ](https://github.com/hmzainjamil) |
| BDM sweep: 08:00 only — respects LinkedIn rate limits and business hours | [HMZ](https://github.com/hmzainjamil) |

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **BDM Lead Sweep** | [Apollo.io](https://apollo.io), [Hunter.io](https://hunter.io), [ZoomInfo](https://zoominfo.com) |
| **Email Sequences** | [Instantly](https://instantly.ai), [Lemlist](https://lemlist.com), [Smartlead](https://smartlead.ai) |
| **LinkedIn Content** | [Buffer](https://buffer.com), [Hootsuite](https://hootsuite.com), [Taplio](https://taplio.com) |
| **Competitor Intel** | [Similarweb](https://similarweb.com), [SEMrush](https://semrush.com), [Ahrefs](https://ahrefs.com) |
| **KPI Monitoring** | [Databox](https://databox.com), [Klipfolio](https://klipfolio.com), [AgencyAnalytics](https://agencyanalytics.com) |

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-n8n-workflows&type=Date)](https://star-history.com/#hmzainjamil/hmz-n8n-workflows&Date)
