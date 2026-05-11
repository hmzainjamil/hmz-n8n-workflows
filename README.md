# hmz-n8n-workflows
Production n8n automation workflows — lead gen, reporting, client onboarding, and agency ops

![n8n](https://img.shields.io/badge/n8n-self--hosted-red?style=flat&labelColor=000) ![Workflows](https://img.shields.io/badge/workflows-production-brightgreen?style=flat&labelColor=555) ![DigiMinds](https://img.shields.io/badge/DigiMinds-Agency_Ops-6C3EE8?style=flat&labelColor=555)

Part of the [HMZ AI Infrastructure](https://github.com/hmzainjamil) stack — the automation backbone of DigiMinds agency.

---

## 🧠 WORKFLOW ARCHITECTURE

| Category | Trigger | Integrations | Output |
|----------|---------|-------------|--------|
| Lead Generation | Daily cron | Apollo + LinkedIn + Instantly | Scored leads → Paperclip BDM |
| Client Reporting | Monthly | GA4 + Google Ads + Meta | PDF report → email |
| Onboarding | Contract signed | Gmail + Notion + Airtable | Welcome pack sent |
| Campaign Launch | PM trigger | GTM + GA4 + Ads APIs | Tracking verified |
| Invoice Processing | 1st of month | Accounting + Gmail | Invoices sent |

## ⚙️ KEY WORKFLOWS

■ **BDM Pipeline**
1. Apollo prospect pull → ICP scoring (50 leads/day)
2. Enrichment → pain-point detection
3. Sequence load → Instantly 5-touch 14-day email
4. Reply detection → Paperclip task creation
5. Discovery call booking → Calendly

■ **Reporting Pipeline**
1. Pull platform data (GA4, Google Ads MCC, Meta)
2. Normalize into template
3. Generate PDF via ReportLab
4. QA verification step
5. Send to client + log to Airtable

## 💡 INTEGRATION MAP

| Platform | Credential | Operations |
|----------|-----------|-----------|
| Apollo | API key | prospect, enrich, sequence |
| Instantly | API key | campaigns, sequences, analytics |
| Google Ads | OAuth | MCC data pull, campaign stats |
| Meta Ads | Token | account insights, creative stats |
| GA4 | Service account | traffic, conversions, events |
| Notion | Integration token | page creation, database updates |
| Gmail | OAuth | send, thread read |

---
Built by [HMZ](https://github.com/hmzainjamil) · [DigiMinds](https://digiminds.org)
