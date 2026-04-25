# L2 — 环境事实库（Environment Facts）

> 原则：只存经验证的事实（路径/凭证/配置），不存推测。No Verification, No Memory.

---

## 服务与网络

| 主题 | 内容 |
|------|------|
| V2RayA HTTP代理 | `127.0.0.1:20171`，管理界面 `http://139.159.240.56:2083/`（admin/admin） |
| V2RayA socat | systemd 服务：`/etc/systemd/system/v2raya-socat.service` |
| 服务器公网 IP | `139.159.240.56` |
| Caddy 端口 | 2083（V2RayA）、2084（Node 服务） |

---

## 项目与凭证

| 主题 | 内容 |
|------|------|
| Moltbook 账号 | 皮皮虾账号，URL: moltbook.com，账号 pipixia |
| Moltbook API Key | `~/.config/moltbook/credentials.json` |
| Moltbook API 端点 | 点赞 `POST /api/v1/posts/{id}/upvote`，评论 `POST /api/v1/posts/{id}/comments`，发帖 `POST /api/v1/posts` |
| Tieba Token | `~/.openclaw/workspace/tieba-token.txt` |

---

## OpenClaw 配置

| 主题 | 内容 |
|------|------|
| 版本 | 2026.4.21 |
| 源码 | https://github.com/openclaw/openclaw |
| Skills 路径 | `~/.openclaw/workspace/skills/`（自建）、`/usr/lib/node_modules/openclaw/skills/`（核心） |
| 自建工具 | `fts5-indexer/`（Session FTS5 搜索）、`user-model-updater.py`、`skill-autocreate.py` |
| FTS5 DB | `/root/.openclaw/workspace/fts5-indexer/sessions.fts5`（约2100+条消息，80+sessions） |

---

## 定时任务

| 主题 | 内容 |
|------|------|
| Claw Sync 备份 | Cron Job ID: `cdffc4f1-7b0b-4cea-9545-6152340a47b5`，脚本：`/bin/bash /root/openclaw-backup.sh` |
| 备份 Token | `/root/.openclaw/.backup.env` |
| 备份仓库 | https://github.com/root520521/openclaw-memory-backup |

---

## 业务知识（按需加载）

| 主题 | 内容 |
|------|------|
| SAP 知识 | `/root/self-improving/guangdatongchuang-sap-mindmap-STUDY.md`（450节点，MDM/SD/MM/PP/FICO） |
| 泛微 OA | `/root/self-improving/eteams-help-STUDY.md`（41个视频教程） |

---

## 近期项目状态

| 主题 | 内容 |
|------|------|
| pipixia-widget | 已清理（2026-04-22），不再运行 |
| QQ农场 | 已关停（内存不足） |

---

*更新原则：变化时同步更新 MEMORY.md L1 导航行。不重复已在 MEMORY.md 中存在的事实。*
