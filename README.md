# offcut

Team-native, mergeable memory for AI coding agents.

Local-first capture with a beautiful viewer. Promote durable judgments (failures, fixes, decisions) into an append-only log that travels with the repo — reviewable in PRs, mergeable across forks, shared across humans and agents.

## Why offcut

claude-mem owns solo episodic capture. projectmem owns judgment events for one developer. offcut aims at the gap between them:

- a polished local viewer (not just a debug firehose)
- multi-human team sync
- fork-mergeable append-only memory (no SQLite-as-source-of-truth)

## Status

Greenfield scaffold. Storage core TBD (leaning JSONL-in-repo + union merge).

## Layout (planned)

```
offcut/
  packages/
    core/      # event log, merge, promote, brief
    viewer/    # localhost UI
    mcp/       # agent tools
  docs/
  examples/
```

## Name

Reuses the stale `offcut` product name on purpose: useful leftover pieces from real work.
