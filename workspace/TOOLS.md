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

# L4 归档：归档14天前的旧会话（压缩后存 L4-sessions/）
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py archive --days 14

# L4 列出已归档会话
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py list-l4

# L4 恢复会话（从归档恢复到活跃目录）
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py restore <session_filename>

# 状态统计
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py stats

# 文件引用展开：{{file:路径:起始:结束}}
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py expand-refs /path/to/file --start 1 --end 20

# 文件访问热度记录
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py touch-access /path/to/file

# 列出文件访问热度
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py list-accessed

# 建议从 L3 升 L2 的文件（本周访问>=5次）
python3 /root/.openclaw/workspace/fts5-indexer/indexer.py suggest-promotions

# 更新用户模型
python3 /root/.openclaw/workspace/user-model-updater.py

# 运行自动技能创建引擎
python3 /root/.openclaw/workspace/skill-autocreate.py
```

## 文件引用语法

在 SOP / MEMO 等文本中引用文件片段，使用：`{{file:路径:起始行:结束行}}`
示例：`{{file:/root/.openclaw/workspace/memory/L2-facts.md:1:20}}`
在回复中会自动展开为带标题边框的片段。

## 自建工具路径

| 工具 | 路径 |
|------|------|
| FTS5 索引+归档 | `/root/.openclaw/workspace/fts5-indexer/` |
| 文件引用展开 | `expand-refs` 子命令 |
| 用户模型 | `/root/.openclaw/workspace/user-model.json` |
| 自动技能引擎 | `/root/.openclaw/workspace/skill-autocreate.py` |
