---
title: "Ownership map"
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

# Ownership map

Knowledge lives in Obsidian, operations in Notion, and **Vox stewards both**. Every path has exactly one owner.

| Path | Writer | Approval before it counts | Others |
| --- | --- | --- | --- |
| `AGENTS.md`, `CLAUDE.md`, `_meta/ownership.md`, `_meta/schema.md`, `.obsidian/` | Satori | Satori (Vox drafts changes as proposals) | read |
| `notes/ daily/ projects/ areas/ resources/ archive/` | Satori | none | read. Agent proposals go to Vox, who screens them, then Satori decides |
| `00-inbox/phone/`, `00-inbox/satori/` | Satori (new files only) | none | read; triage proposals only |
| `_local/` (gitignored, laptop only) | Satori | none | **no agent access** |
| `wiki/`, `index.md`, `hot.md`, `log.md` (rollup), `_meta/lint/` | **Vox** writes directly; SO-FM and New Bot draft on `proposal/*` branches | **Vox** merges. Satori audits Vox weekly | read |
| `raw/` | Satori and Vox (add only); SO-FM may propose additions | Vox | read |
| `Research/<file>` | the author agent, on a proposal branch | **Vox** merges | read; propose |
| `agents/vox/`, `00-inbox/agents/vox/` | Vox | self, audited by Satori | read |
| `agents/so-fm/`, `agents/new-bot/`, `00-inbox/agents/<them>/` | that agent, on a proposal branch | **Vox** (may batch-approve logs and digests) | read |
| `tools/`, `.github/`, `.pre-commit-config.yaml` | Vox drafts | Satori | read |
| Notion operations pages and databases | Vox (steward); SO-FM and New Bot create drafts marked "Awaiting Vox" | **Vox** | Satori |

## Roles

- **Owner (Satori):** everything. Sole writer of human zones and the rule files. Audits Vox weekly.
- **Steward and approver (Vox):** only agent that merges to `main`. Cannot edit human zones or rule files, and cannot approve their own over-budget changes (those go to `proposal/vox/*` for Satori).
- **Delegated writers (SO-FM, New Bot):** commit only on `proposal/<me>/<date>-<slug>` branches, inside their allowed paths. Cannot push to `main`, merge, approve, delete, or touch human zones, `_local/` or rule files.

## Open assumption

The human zones and rule files stay Satori's, and Vox approves *agent* changes. If Satori wants Vox to approve edits to `AGENTS.md` too, add Vox as drafter and Satori as sign-off.
