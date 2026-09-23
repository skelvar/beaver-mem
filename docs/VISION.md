# Vision

## Problem

Agent memory today is either:

1. Personal episodic capture (claude-mem style) — great alone, weak for teams/forks
2. Solo judgment logs (projectmem style) — local-first but single-user by design

Teams still lose context across humans, agents, and forks.

## Product

offcut = beautiful local memory studio + reviewable shared memory that merges like code.

### Pillars

1. **Local viewer** — inspect, pin, deprecate, preview what agents will inject
2. **Promote** — turn private session noise into typed team events
3. **Append-only log** — immutable events; corrections supersede; views rebuild
4. **Git-native sync** — PR review, fork union-merge, blame/authorship

### Non-goals (v0)

- Replacing claude-mem capture quality on day one
- Cloud-hosted memory SaaS
- Vector DB as source of truth
