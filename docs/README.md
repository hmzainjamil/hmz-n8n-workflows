# Documentation index

| Document | Role | Evidence and limits |
|---|---|---|
| [Repository README](../README.md) | Archive purpose, snapshot inventory, safe import steps | Tree count as of 2026-10-02; no workflow runs claimed |
| [Security policy](../SECURITY.md) | Private vulnerability reporting and secret handling | Does not claim version support or security certification |
| [Workflow archive](../workflows/) | Exported JSON and metadata | Review each file; folder names are not execution evidence |

## Import review

Before importing, check each export for credentials, personal data, webhook exposure, node availability, destinations, and write/send behavior. Test in an isolated n8n environment with synthetic data before enabling. Keep upstream attribution and license terms.
