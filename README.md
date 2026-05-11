# hmz-n8n-workflows
production automation workflows — every DigiMinds operation that shouldn't require a human

![n8n](https://img.shields.io/badge/n8n-self--hosted-red?style=flat&labelColor=000) ![Workflows](https://img.shields.io/badge/workflows-production-brightgreen?style=flat&labelColor=555) ![Integrations](https://img.shields.io/badge/integrations-20%2B_apps-blue?style=flat&labelColor=555) ![DigiMinds](https://img.shields.io/badge/DigiMinds-Agency_Ops-6C3EE8?style=flat&labelColor=555)

DigiMinds n8n automation workflows — every repeatable agency operation that doesn't need a human. Lead processing, client reporting, invoice handling, content publishing, competitor monitoring. Self-hosted for data privacy. All workflows are idempotent, have error notifications, and write to Notion/Paperclip for audit trails.

[Workflow Inventory](#inventory) · [Integration Map](#integrations) · [n8n Setup](#setup) · [Design Patterns](#patterns) · [Tips](#tips) · [Gotchas](#gotchas)

## 🧠 WORKFLOW INVENTORY

<a id="inventory"></a>
■ **Client Operations**

| Workflow | Trigger | Chain | SLA |
|---|---|---|---|
| Lead Intake → CRM | Typeform webhook | Typeform → Apollo enrich → HubSpot create → Slack | <2min |
| Weekly Performance Report | Mon 9:00 AM cron | GA4 → Google Ads → ReportLab PDF → Gmail → Notion | 9:00-9:15 AM |
| Monthly Invoice Generator | 1st of month cron | HubSpot deals → Stripe create → PDF → Gmail send | <5min |
| Client Onboarding Checklist | HubSpot deal stage change | Trigger on "Closed Won" → Notion task list → Slack → Gmail intro | <1min |
| NPS Survey Dispatcher | Monthly cron (day 15) | HubSpot → email list filter → Typeform link → track responses | <5min |

■ **Business Development**

| Workflow | Trigger | Chain | SLA |
|---|---|---|---|
| LinkedIn Lead Enricher | Daily 8:00 AM | Apollo API → lead list → score 0-100 → HubSpot upsert | 8:00-8:20 AM |
| Competitor Price Monitor | Daily 10:00 AM | Web scrape 5 competitor sites → compare prev → Notion → Slack if changed | 10:00-10:10 AM |
| Indeed Job Monitor | Daily 7:30 AM | Indeed RSS → filter (AU, $15+/hr) → Paperclip task create | 7:30-7:35 AM |
| Proposal Sent Tracker | Gmail trigger | Detect "proposal" in sent email → HubSpot update → follow-up task | <30s |

■ **Content Operations**

| Workflow | Trigger | Chain | SLA |
|---|---|---|---|
| LinkedIn Post Publisher | File watch (~/Downloads/linkedin-post-*.txt) | Read file → LinkedIn API post → track URL → Notion log | <1min after file created |
| Blog Publisher | Notion status change ("Ready") | Fetch content → format → WordPress/Ghost publish → social share | <3min |
| Content Calendar Builder | Weekly Mon 8 AM | Trend data → GPT-4o-mini draft → Notion calendar populate | <10min |

■ **Finance & Admin**

| Workflow | Trigger | Chain | SLA |
|---|---|---|---|
| Invoice Processor | Gmail trigger (subject: "invoice") | Parse PDF → Stripe lookup → QuickBooks categorize → Slack | <2min |
| Expense Tracker | Daily 6 PM | Pull Stripe/PayPal transactions → categorize → Notion → alert if anomaly | Daily |
| Runway Calculator | Weekly Sun 11 PM | QuickBooks revenue/expense → calculate runway months → Slack report | Weekly |

<a id="integrations"></a>
## ⚙️ INTEGRATION MAP

| Service | Auth Type | Used In | Credentials |
|---|---|---|---|
| Google Analytics 4 | OAuth2 | Reporting workflows | `N8N_GA4_OAUTH` |
| Google Ads | OAuth2 | Reporting, performance data | `N8N_GADS_OAUTH` |
| Meta Ads | OAuth2 | Reporting, creative performance | `N8N_META_OAUTH` |
| HubSpot | API Key | Lead intake, deal tracking | `N8N_HUBSPOT_KEY` |
| Apollo.io | API Key | Lead enrichment | `N8N_APOLLO_KEY` |
| Stripe | API Key | Invoice, payment processing | `N8N_STRIPE_KEY` |
| QuickBooks | OAuth2 | Expense tracking, invoicing | `N8N_QB_OAUTH` |
| Notion | API Key | Logging, task creation | `N8N_NOTION_KEY` |
| Gmail | OAuth2 | Email trigger, sending | `N8N_GMAIL_OAUTH` |
| LinkedIn | OAuth2 | Content publishing | `N8N_LINKEDIN_OAUTH` |
| Slack | OAuth2 | Alerts, notifications | `N8N_SLACK_OAUTH` |
| Typeform | Webhook | Lead intake, surveys | Webhook URL |
| WordPress | API Key | Blog publishing | `N8N_WP_KEY` |

<a id="setup"></a>
## 💡 N8N SETUP

**Self-hosted config** (`~/.n8n/config`):
```
N8N_HOST=localhost
N8N_PORT=5678
N8N_PROTOCOL=http
N8N_ENCRYPTION_KEY=<random-32-char>
EXECUTIONS_DATA_MAX_AGE=168   # 7 days retention
```

**LaunchAgent** (persistent service):
```bash
# n8n runs as a LaunchAgent for always-on operation
# Working dir: ~/installed-repos/n8n
# Log: ~/Library/Logs/n8n.log
```

**Access:** `http://localhost:5678`

**Backup workflows:**
```bash
# Export all workflows
n8n export:workflow --all --output=~/Downloads/n8n-backup-$(date +%Y%m%d).json

# Import backup
n8n import:workflow --input=n8n-backup.json
```

<a id="patterns"></a>
## 🔧 DESIGN PATTERNS

■ **Error Handling (every workflow must have)**

```
All workflows:
  ↓ Error node (catch any failure)
  ↓ Slack notification (channel: #automation-errors)
  ↓ Notion error log (table: Automation Errors)
  ↓ Retry 3x with 5s backoff (for API errors)
```

■ **Idempotency**
```
Lead intake: check HubSpot contact exists before creating
Reporting: check if report already sent for this period
Invoice: check Stripe invoice ID before creating duplicate
Content: check Notion status before publishing
```

■ **Audit Trail**
Every workflow writes a completion record to Notion:
```json
{
  "workflow": "weekly-report",
  "run_at": "2026-05-12T09:00:00Z",
  "status": "success",
  "records_processed": 3,
  "outputs": ["report-client-a.pdf", "report-client-b.pdf"]
}
```

<a id="tips"></a>
## 🧠 TIPS

| Tip | Note |
|---|---|
| Use `Wait` node instead of `Sleep` in n8n — Sleep blocks the execution thread, Wait yields it | Critical for multi-step workflows |
| Split large batch operations into chunks of 10 — most APIs rate-limit at 100 req/min | Use `Split In Batches` node |
| Store OAuth tokens in n8n credential manager, not env vars — env vars don't refresh on expiry | n8n auto-refreshes OAuth in credential manager |
| Add webhook authentication for all external-facing webhooks — Typeform supports HMAC signatures | `N8N_WEBHOOK_SECRET` in Typeform settings |
| Use `IF` node before any write operation to verify data exists — prevents blank records | Null check before HubSpot/Notion writes |
| Test workflows with `Execute Workflow` button in manual mode before activating — catches bad credentials early | |
| Set `Error Workflow` in workflow settings — this runs automatically on any uncaught error | |
| Export workflows weekly via `n8n export:workflow --all` — self-hosted n8n has no auto-backup | Add to LaunchAgent rotation |

<a id="gotchas"></a>
## ☠️ GOTCHAS

| Gotcha | Fix |
|---|---|
| n8n OAuth tokens expire silently — workflows fail with 401 but no clear error | Set calendar reminder every 55 days to re-auth all OAuth creds |
| Webhook URLs change when n8n restarts with different port — all external services need updating | Always use port 5678 and set `N8N_HOST` explicitly |
| n8n `Code` nodes with `require()` fail on self-hosted — n8n sandboxes JS | Use built-in nodes or HTTP Request node for external calls |
| Google Analytics 4 node returns data in UTC — client reports may show wrong date for AEST clients | Convert TZ in Code node: `new Date(date).toLocaleString('en-AU', {timeZone: 'Australia/Sydney'})` |
| HubSpot rate limit is 100 req/10s — batch lead imports hit this | Add `Wait 100ms` node between each HubSpot API call |
| Typeform webhooks retry on failure — duplicate submissions if workflow is slow | Add dedup check by Typeform response ID |

## 📁 WORKFLOW FILES

```
hmz-n8n-workflows/
├── client-ops/
│   ├── lead-intake-crm.json
│   ├── weekly-performance-report.json
│   ├── monthly-invoice-generator.json
│   └── client-onboarding-checklist.json
├── bdm/
│   ├── linkedin-lead-enricher.json
│   ├── competitor-price-monitor.json
│   └── indeed-job-monitor.json
├── content/
│   ├── linkedin-post-publisher.json
│   └── blog-publisher.json
├── finance/
│   ├── invoice-processor.json
│   └── expense-tracker.json
└── templates/
    ├── error-handler.json       ← base error handling template
    └── audit-log.json           ← base audit trail template
```
