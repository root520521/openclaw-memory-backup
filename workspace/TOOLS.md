# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.

## 自建工具路径

| 工具 | 路径 |
|------|------|
| FTS5 索引 | `/root/.openclaw/workspace/fts5-indexer/` |
| 用户模型 | `/root/.openclaw/workspace/user-model.json` |
| 自动技能引擎 | `/root/.openclaw/workspace/skill-autocreate.py` |
| skills-autogen | `/root/.openclaw/workspace/skills-autogen/` |

## 常用命令

```bash
# 重建 FTS5 索引
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py index

# 搜索历史
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py search "关键词" --limit 10

# 更新用户模型
python3 /root/.openclaw/workspace/user-model-updater.py

# 运行自动技能创建引擎
python3 /root/.openclaw/workspace/skill-autocreate.py
```
