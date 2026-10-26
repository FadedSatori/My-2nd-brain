---
title: "Frontmatter schema"
type: note
author: satori
author_type: human
created: 2026-10-26
updated: 2026-10-26
status: draft
classification: internal
approved_by: ""
sources: ["https://app.notion.com/p/403f6c73e1078149883fd9ad8d3f3290"]
tags: [meta]
---

# Frontmatter schema

```yaml
---
title: "..."
type: note | source | wiki | research | proposal | digest | log
author: satori | vox | new-bot | so-fm
author_type: human | agent
created: 2026-10-24
updated: 2026-10-24
status: draft | approved | verified | archived   # agents set draft; Vox's merge sets approved; Satori sets verified
classification: internal  # public | internal | sensitive | restricted; missing = internal
approved_by: ""          # "vox" once Vox merges; "satori" for human-zone items
sources: []            # URLs or [[raw/...]] links. REQUIRED for agent notes beyond draft
derived_from: []       # [[notes]] this was synthesized from (provenance chain)
confidence: low | medium | high
review_by: 2027-01-24  # agent notes: created + 90 days
source_url: ""         # for raw/ items
archived_url: ""       # web archive copy, if any
tags: []
---
```

## Lint rules

- `author_type: agent` with an empty `sources` field fails unless `status: draft`.
- `status: approved` must arrive in a Vox merge commit carrying `Approved-by: vox`; `verified` must come from a Satori commit.
- `approved_by` must be set whenever `status` is above `draft`.
- `classification: restricted` or `sensitive` in any committed file fails. The repo holds pointers only.
- `review_by` in the past goes into the weekly digest.

## Classification

| Level | Meaning | In the vault | Agents |
| --- | --- | --- | --- |
| `public` | Fine to publish | anywhere | read/write |
| `internal` (default) | Normal notes and non-confidential work | anywhere | read; write via the normal zones and Vox's approval |
| `sensitive` | Third-party people research, client-confidential summaries, Satori's private notes | pointer only. The note lives in Notion's restricted section, offline, or in `_local/` | Notion copy readable through connectors; `_local/` no access |
| `restricted` | Credentials, account numbers, health and legal records, IDs | pointer only. The note lives in the password manager or offline encrypted storage | never |

Pointer format: `→ RESTRICTED: 1Password › Personal › "Passport"` or `→ SENSITIVE: Notion › People Research › case 12`. A pointer names where something is, never what it is.
