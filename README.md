# n8n Workflow Archive

A large collection of exported n8n workflow JSON files. The Git tree checked on 2026-10-02 contains 8,313 JSON files in 8,134 folders under `workflows/`. These are file counts only: they do not establish that each file is a complete workflow, imports cleanly, or runs successfully.

## Scope

| Item | Evidence |
|---|---|
| Main content | Exported JSON and metadata beneath `workflows/` |
| Runtime | No n8n instance or execution service is included in this repository |
| Compatibility | Check each export against your installed n8n version and required node packages |
| Verification | No workflows were imported or executed for this documentation change |
| Security | Each export needs review for credentials, personal data, webhooks, and external side effects |

The collection includes workflows for many services and tasks. Folder names are descriptive labels, not validation results. Use GitHub's [workflow folders](workflows/) to browse the archive.

## Import carefully

1. Inspect the workflow JSON and associated metadata.
2. Confirm the workflow's nodes, credential types, webhook paths, input data, external destinations, and write/send actions.
3. Import into a non-production n8n instance or isolated workspace.
4. Add credentials through n8n's credential manager; do not put secrets in exported JSON.
5. Test with synthetic data, review execution logs, and keep the workflow inactive until approved.

A workflow may send email, alter records, post publicly, call external APIs, or expose a webhook. Review and test those effects before activation.

## Documentation and security

See the [documentation index](docs/README.md) and [security reporting guidance](SECURITY.md). Report a suspected credential exposure through a private channel; do not include secrets in public issues.

## Maintenance

Keep source attribution and license terms with imported material. When updating counts, derive them from the repository tree and record the date. Report import or execution results only after testing against a stated n8n version and configuration.
