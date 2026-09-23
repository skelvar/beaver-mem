# beaver-mem

Team-native, mergeable memory for AI coding agents.

Local-first capture with a beautiful viewer. Promote durable judgments (failures, fixes, decisions) into an append-only log that travels with the repo — reviewable in PRs, mergeable across forks, shared across humans and agents.

## The idea

claude-mem owns solo episodic capture. projectmem owns judgment events for one developer. beaver-mem targets the gap:

- a polished local viewer (not just a debug firehose)
- multi-human team sync via git
- fork-mergeable append-only memory (JSONL is source of truth; SQLite is a local cache only)

Teammates get memory **files** by pulling the repo even without installing beaver-mem. Agent features (inject, promote, precheck, viewer) need the tool installed.

## Status

Greenfield. Roadmap: [docs/ROADMAP.md](docs/ROADMAP.md). Vision: [docs/VISION.md](docs/VISION.md). Storage: [docs/STORAGE.md](docs/STORAGE.md).

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

`beaver-mem` — beaver mascot + memory. Avoids collisions with bare `beaver` / `kerf` / Bashar's existing `offcut` product.
