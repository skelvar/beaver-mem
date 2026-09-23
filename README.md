# beaver-mem

Team-native, mergeable memory for AI coding agents.

Local-first capture with a beautiful viewer. Promote durable judgments (failures, fixes, decisions) into an append-only log that travels with the repo — reviewable in PRs, mergeable across forks, shared across humans and agents.

## Why beaver-mem

claude-mem owns solo episodic capture. projectmem owns judgment events for one developer. beaver-mem aims at the gap between them:

- a polished local viewer (not just a debug firehose)
- multi-human team sync
- fork-mergeable append-only memory (no SQLite-as-source-of-truth)

## Status

Greenfield scaffold. Storage core TBD (leaning JSONL-in-repo + union merge).

## Layout (planned)

```
beaver-mem/
  packages/
    core/      # event log, merge, promote, brief
    viewer/    # localhost UI
    mcp/       # agent tools
  docs/
  examples/
```

## Name

beaver-mem — the beaver mascot + memory. Deliberately not named after other agent tools that already own crowded brands.
