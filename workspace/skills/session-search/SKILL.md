---
name: session-search
description: "FTS5 full-text search across OpenClaw session history. Use when Kevin asks about past conversations, previous tasks, or anything that happened in earlier sessions."
---

# Session Search Skill

Search OpenClaw session history using FTS5 full-text search.

## Usage

```bash
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py search "关键词" --limit 10
```

## Examples

```bash
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py search "V2RayA" --limit 5
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py search "QQ农场" --limit 10
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py search "snap" --role user --limit 5
```

## Components

- Indexer: `/root/.openclaw/workspace/fts5-indexer/indexer.py`
- SQLite DB: `/root/.openclaw/workspace/fts5-indexer/sessions.fts5`
- Indexed: 58 sessions, 764 messages

## Rebuild Index

```bash
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py index
```
