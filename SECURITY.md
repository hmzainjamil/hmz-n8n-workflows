# Security policy

This repository stores exported workflow definitions. A workflow can contain endpoint details, webhook paths, expressions, personal data, or actions that write to external systems. Treat every export as untrusted until reviewed.

## Reporting a vulnerability

Do not publish credentials, private workflow exports, or exploit details in a public issue. Use GitHub's private vulnerability reporting feature if it is enabled for this repository. Otherwise, contact the maintainer through the current private contact method on the [maintainer's GitHub profile](https://github.com/hmzainjamil).

Include the affected file or workflow identifier, impact, and safe reproduction details. Redact tokens and personal data. Do not assume a response time or supported-version range unless the maintainer publishes one.

## Safe handling

- Store credentials in n8n's credential manager, never in exported workflow JSON or Git.
- Review webhooks, external hosts, recipients, and write actions before enabling a workflow.
- Rotate any exposed credential and remove it from active use; deleting it from a later commit does not erase prior Git history.
- Test imported workflows in an isolated instance with synthetic data before production use.

This policy does not certify the collection or individual workflows as secure.
