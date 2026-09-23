# Event log (draft)

Source of truth is append-only JSONL under `.offcut/log/YYYY/MM/DD.jsonl`.

Each line is one immutable event, e.g.:

```json
{
  "id": "01J...",
  "type": "failure|attempt|fix|decision|note|promote",
  "ts": "2026-09-23T09:00:00Z",
  "author": { "human": "bashar", "agent": "claude-code" },
  "repo": "owner/name",
  "branch": "feat/x",
  "commit": "abc123",
  "paths": ["src/auth.ts"],
  "summary": "JWT refresh raced with logout",
  "detail": "...",
  "supersedes": null,
  "visibility": "local|team"
}
```

Merge rule: union of lines by `id`, sort by `id`. Never rewrite history.
Projections (brief, failure index, SQLite cache, embeddings) rebuild from the log.
