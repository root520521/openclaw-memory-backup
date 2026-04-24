---
name: user-model
description: "Query Kevin's structured user model. Run automatically or on demand."
---

# User Model Skill

Query Kevin's structured user model to understand context.

## Read Model

```bash
cat /root/.openclaw/workspace/user-model.json
```

## Update Model (手动)

```bash
python3 /root/.openclaw/workspace/user-model-updater.py
```

## Model Schema

```json
{
  "updated": "ISO timestamp",
  "topics": ["SAP", "泛微OA", ...],
  "active_projects": ["Moltbook学习", "V2RayA代理", ...],
  "preferences": { "简洁": true, "技术背景": true },
  "last_topics": [...],
  "notes": [{ "ts": "...", "note": "..." }]
}
```

## Usage

Before responding to Kevin, check this model if the conversation touches known topics or projects.

Example queries:
- "Kevin 最近的活跃项目是什么？"
- "他配置过哪些技术栈？"
- "他对简洁有什么偏好？"
