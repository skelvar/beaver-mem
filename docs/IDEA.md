# Project idea (brief)

## One sentence

beaver-mem is git-native team memory for AI coding agents: an append-only, PR-reviewable log of failures/fixes/decisions, plus a local studio to curate what agents should remember.

## Problem (facts that motivated this)

- Solo tools (claude-mem, projectmem) help one developer across sessions but are weak for multi-human and fork merge.
- SQLite-as-source-of-truth does not merge cleanly across branches/forks.
- Teams still lose “what we already tried” inside private agent chats.
- Reddit/X pain (Sep 2026 research): error loops, amnesia, cross-agent chaos; memory category is hot but team+fork product is under-won.

## Solution shape

| Layer | Role |
|---|---|
| JSONL log in `.beaver-mem/` | Source of truth, git-synced, union-merge by event `id` |
| SQLite cache (gitignored) | Fast local search for viewer |
| CLI + MCP + hooks | Agent read/write/promote |
| Local viewer | Human curation, inject preview, conflicts |
| Optional AGENTS.md export | Tiny benefit for agents without beaver-mem installed |

## Differentiation

- vs **claude-mem**: not primarily auto episodic capture; team promote + merge + studio
- vs **projectmem**: multi-human/forks first-class; beautiful viewer; same judgment vocabulary welcome via import later
- vs **gitmem / grite / team-memory**: beaver-mem aims at the **product** (viewer + promote UX + agent harness install path), not only the log mechanics

## Success metrics (early)

1. Two branches can append events and merge with zero manual JSON conflict resolution in the happy path.
2. Session-start brief is useful enough that a developer stops pasting “project context” by hand.
3. Someone uses the viewer to deprecate bad memory instead of deleting log lines.

## Out of scope for v0

Cloud sync service, marketplace, replacing existing capture plugins entirely.
