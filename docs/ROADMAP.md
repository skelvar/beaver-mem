# Roadmap

Living plan for beaver-mem. Dates are target windows, not promises.

## North star

A team can share agent-learned failures, fixes, and decisions the same way they share code: commit, PR, merge, fork — with a beautiful local studio to inspect and promote memory.

## Principles

1. JSONL append-only log under `.beaver-mem/` is the **source of truth** (git-synced, reviewable, mergeable).
2. SQLite (or similar) is a **gitignored local projection** for search/UI speed — never merged.
3. Corrections **supersede**; history is never rewritten.
4. Partial adoption works: no install required to *receive* files; install required for agent features.
5. Do not collide with claude-mem (solo episodic) or projectmem (solo judgment) — complement them; optionally import later.

---

## Phase 0 — Foundations (now)

**Goal:** Repo, docs, and locked product shape so another agent can implement without re-litigating design.

- [x] Name: `beaver-mem`
- [x] Local scaffold at `D:\work\beaver-mem`
- [x] Vision + storage draft
- [x] This roadmap committed and pushed to `skelvar/beaver-mem`
- [ ] Event schema v0 frozen in `docs/STORAGE.md` (fields, types, supersedes, visibility)
- [ ] Union-merge rules written (by `id`, sort, duplicate verify)
- [ ] Non-goals explicit (no cloud SaaS v0, no vector DB as source of truth)

**Exit:** A new contributor can explain the product in one paragraph and know what not to build.

---

## Phase 1 — Core log + CLI (MVP)

**Goal:** Append, read, brief — no UI yet.

- [ ] `packages/core`: append event, validate schema, read log, build token-budgeted **brief**
- [ ] CLI: `beaver-mem init`, `append`, `brief`, `verify`
- [ ] `beaver-mem init` creates `.beaver-mem/` layout + `.gitignore` entries for cache
- [ ] Git merge driver (or documented union strategy) for day files
- [ ] Unit tests for merge / supersede / verify
- [ ] Example fixture repo under `examples/`

**Exit:** In a sample repo you can append a failure + fix, run `brief`, and merge two branches without losing events.

---

## Phase 2 — Agent wiring

**Goal:** Coding agents can read and write memory.

- [ ] MCP server (`packages/mcp`): `memory_brief`, `memory_append`, `memory_search`, `memory_precheck_path`, `memory_conflicts`
- [ ] Session-start hook / skill snippet for Claude Code + Cursor (inject brief)
- [ ] **Promote** command: turn a local/private note into `visibility: team` event
- [ ] Authorship fields always set (human, agent harness, branch, commit when known)
- [ ] Optional export: generate a short `AGENTS.md` / `CLAUDE.md` block from team events (dumb fallback for agents without beaver-mem)

**Exit:** Claude Code or Cursor on a beaver-mem repo starts a session already knowing recent team decisions/failures.

---

## Phase 3 — Local viewer (the wedge)

**Goal:** Beautiful localhost studio — not a firehose.

- [ ] `packages/viewer`: local web app (SSE or poll)
- [ ] Timeline of events with author, type, paths
- [ ] Pin / deprecate / supersede from UI
- [ ] Preview: “what will be injected next session”
- [ ] Conflict inbox (contradictory decisions)
- [ ] Rebuild SQLite cache from JSONL on open
- [ ] Team vs local visibility filter

**Exit:** A human prefers the viewer over reading raw JSONL when curating memory.

---

## Phase 4 — Team + forks

**Goal:** Multi-human sync feels boring (in a good way).

- [ ] Document team workflow: promote → commit → PR → merge
- [ ] Fork compare view: “only on your fork” vs “upstream”
- [ ] Conflict queue UX + resolve via supersede event
- [ ] CODEOWNERS / review tips for `.beaver-mem/`
- [ ] Redaction on promote (secrets/PII scan)
- [ ] Import adapters (optional): projectmem events, claude-mem export → beaver-mem types

**Exit:** Two developers on two forks can both append, open a PR, merge, and both agents see the union.

---

## Phase 5 — Polish + release

**Goal:** Public npm + docs people can trust.

- [ ] npm package `beaver-mem`
- [ ] Install docs for Claude Code, Cursor, Codex
- [ ] Performance pass on brief budgeting
- [ ] Dogfood on a real multi-dev repo
- [ ] v0.1.0 tag

---

## Explicit non-goals (near term)

- Replacing claude-mem’s automatic full-session capture on day one
- Hosted cloud memory product
- Vector DB as the merged source of truth
- Requiring every teammate to install beaver-mem just to keep the repo valid
- Bare names `beaver`, `kerf`, or `offcut` (collisions / existing products)

## Open decisions (for implementers)

1. Language for core: TypeScript (ecosystem fit with agent tooling) vs Rust (merge driver / speed) — default lean **TypeScript** unless profiling says otherwise.
2. Day-file partitioning: `log/YYYY/MM/DD.jsonl` (gitmem-style) vs single `events.jsonl` — default **daily files**.
3. Whether v0 ships the git merge driver installed automatically or as `beaver-mem merge-driver install`.

## Suggested first implementation slice

After this doc is on GitHub: freeze schema → `init` + `append` + `brief` + `verify` + merge test → then MCP brief injection.

