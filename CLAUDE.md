# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is a **documentation-only repository** (separate git repo, `origin` → `github.com/That-is-so-sweet/PRD.git`) containing the product/spec documents for 揪甘心 ("Jiu-Gan-Xin"), a meetup-time-coordination product. There is no source code, no build tooling, and no test runner here — it's a nested folder inside the sibling prototype codebase (`../CLAUDE.md`, one directory up) but tracked as its own repository. Work in this repo means editing/organizing Markdown docs, not writing or running code.

## Document architecture

Docs are split into two tiers by audience, indexed from [README.md](README.md):

- **`產品規劃/`** (product planning) — narrative, for any audience: the problem, users, why now, how success is measured ([產品概觀.md](產品規劃/產品概觀.md)), plus open questions and phased roadmap/prioritization ([開放問題與規劃.md](產品規劃/開放問題與規劃.md)).
- **`開發規格/`** (engineering spec) — implementation-grade detail engineers build/test against:
  - [功能需求.md](開發規格/功能需求.md) — full BDD/Gherkin User Stories (each Scenario: one `Given`/`When`/`Then`, exceptions split into separate scenarios).
  - [規格書.md](開發規格/規格書.md) — the FR-numbered requirements table, DB schema, API design, security, non-functional requirements, open questions. This is the formal engineering spec ("v2").
  - [流程圖.md](開發規格/流程圖.md) — Mermaid flowcharts (main flow + event status transitions), nodes annotated with FR numbers matching 規格書.md §4.1.
  - [頁面規格/](開發規格/頁面規格/README.md) — the *same* Phase 1 business rules re-sliced by screen/modal instead of by feature, to answer "how many screens/modals do we need to build." Adds no new rules.

**Precedence rule**: 功能需求.md and 規格書.md are the source of truth. 頁面規格/ only reorganizes their content by screen — if it ever conflicts with those two, they win. Phase 1 scope must stay consistent across all documents.

**Critical constraint — do not use the prototype as a spec reference**: 規格書.md explicitly states this is a from-scratch formal spec, *not* a transcription of the existing frontend-only prototype (in the sibling repo one level up). Validation rules, identity/auth mechanism, and data model were deliberately redesigned and differ from the prototype's actual behavior. When editing engineering-spec docs, do not resolve ambiguity by looking at the prototype's code/UI — 規格書.md and 功能需求.md are authoritative on their own. (頁面規格/'s screen *inventory*, by contrast, is intentionally derived from the prototype's existing screens as a reference baseline — only the screen list, not visual design or business rules.)

## Conventions when editing

- Every doc file starts and ends with breadcrumb navigation links (`[← 上一部分：...]` / `[PRD 索引](...)`) back to adjacent docs and the README index — preserve this pattern when adding or restructuring docs.
- FR numbers (規格書.md) and User Story numbers (功能需求.md) are cross-referenced by anchor links across nearly every document; when renumbering or renaming a section, grep for the old anchor text across the repo and update all inbound links.
- 開放問題與規劃.md's prioritization scores are explicitly marked as a single-person draft, not a team consensus — don't present them as decided.
