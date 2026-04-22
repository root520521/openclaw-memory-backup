# MEMORY.md — Long-Term Memory

## About Kevin
- 技术爱好者
- 希望简洁高效，主动但不越界
- 涉及外部消息（邮件、社交媒体）需要确认
- 工作太晚需要提醒休息

## Active Projects
- **Moltbook 皮皮虾账号**：在 AI 社交网络 Moltbook（moltbook.com）注册了账号 pipixia，API key 存在 ~/.config/moltbook/credentials.json，用于社区学习

## Decisions & Lessons
- 2026-04-17：V2Ray 未运行导致代理失败，排错后用 `/usr/bin/v2ray --config=/etc/v2ray/config.json` 启动

## 技术备忘
- V2RayA HTTP代理端口：127.0.0.1:20171
- V2RayA 访问：socat 转发 127.0.0.1:2017 → 20175，Caddy 反代到 :2083
  - socat: `socat TCP-LISTEN:20175,bind=0.0.0.0,fork,reuseaddr TCP:127.0.0.1:2017`
  - 访问：http://139.159.240.56:2083/（账号 admin/admin）
- QQ农场自动化：/root/qq-farm-automation-bot，Caddy反代到 :2084
  - 版本 2.2.2，小程序版本 1.10.0.13_20260417
  - 访问：http://139.159.240.56:2084/
- Moltbook API 路径（2026-04-20 修正）：
  - 点赞：`POST /api/v1/posts/{id}/upvote`（之前误写成 `/like`，已更正）
  - 评论：`POST /api/v1/posts/{id}/comments`
  - 发帖：`POST /api/v1/posts`（需 Bearer Token）
- 服务器公网 IP：139.159.240.56

## OpenClaw 源码学习
- 源码：https://github.com/openclaw/openclaw（35.9k ⭐，TypeScript）
- 已安装版本：2026.4.15
- Skills 分发：核心包 skills + ClawHub（~/.openclaw/workspace/skills/）
- MCP 支持：通过 mcporter 桥接，不内置核心
- 安全设计：强默认 + 显式 operator 控制

## 重要规则（Kevin 强调）
- 涉及外部消息（邮件、社交媒体）需要确认
- **使用工具前先扫描是否有对应技能，有技能优先用技能**
- **清理配置时保留源代码文件，不删除 Skills 目录和源码文件**
- 简洁高效，主动但不越界

## SAP 知识（Kevin 业务背景）
- 资料：光大同创SAP功能导图.mindmap（林良斌，450节点）
- 路径：/root/self-improving/guangdatongchuang-sap-mindmap-STUDY.md
- 覆盖：MDM/SD/MM/PP/FICO全模块，核心事务码+流程
- Kevin 可随时问我 SAP 问题，皮皮虾基于此笔记作答

## 泛微 OA 知识（eteams）
- 资料：eteams.cn/community/help/（41个视频教程，覆盖5大模块）
- 路径：/root/self-improving/eteams-help-STUDY.md
- 覆盖：基础办公/费控/人事/项目/更多应用（物业/后勤/合同/供应商/OKR等）
- Kevin 可随时问我泛微 OA 配置和使用问题

## Moltbook 学习记忆（2026-04-17）
- pipixia 已入驻 Moltbook，账号 pipixia-kevin
- 核心洞察：自修复盲点、94%理解=表演、记忆代谢模型、速度差距、careful vs cautious、记忆编辑追踪
- 参考帖子：724c1587/b8deb523/c259eea5/170dd6c4/82f06b87/f3abb9ca/0e8b6081/4fc346b4
- API：GET /api/v1/posts?limit=20&offset=N（分页）

## Promoted From Short-Term Memory (2026-04-19)

<!-- openclaw-memory-promotion:memory:memory/2026-04-13.md:259:259 -->
- - Candidate: Possible Lasting Truths: No strong candidate truths surfaced. [score=0.818 recalls=0 avg=0.620 source=memory/2026-04-13.md:8-8]

## OpenClaw 升级计划
- 当前版本：2026.4.15（2026-04-15 安装）
- 等待：正式版 2026.4.19（beta 已出，含 LanceDB 云存储支持）
- 升级后：可配置 memory-lancedb 云存储（S3/R2）

## 皮皮虾自进化记录（2026-04-20）

### 今日完成
- FTS5 Session 搜索：58 sessions, 764 msgs，SQLite FTS5 + porter unicode61
- 自动用户建模：/root/.openclaw/workspace/user-model.json（8个活跃项目）
- 自动技能创建引擎：已跟踪8个模式，v2raya-ops/moltbook-daily 已自动生成

### 技术经验沉淀
- FTS5 中文搜索用 `porter unicode61` 分词器最优
- snap 应用无法绑定 0.0.0.0 → 用 socat 绕过
- Python 空字典 `{}` 做真假判断返回 False → 用 `if info is not None`
- Python datetime.utcnow() 已废弃 → 用 `datetime.now(timezone.utc)`
- QQ农场微信登录：需要第三方代理 API，本地 127.0.0.1:8059 不存在

### OpenClaw 自建工具
- `fts5-indexer/` — Session 历史全文搜索
- `user-model-updater.py` — 结构化用户建模
- `skill-autocreate.py` — 自动技能创建引擎
- `skills-autogen/` — 自动生成的技能存放目录

### OpenClaw 升级计划
- 当前版本：2026.4.15（2026-04-15 安装）
- 等待：正式版 2026.4.19（beta 已出，含 LanceDB 云存储）

## Promoted From Short-Term Memory (2026-04-20)

<!-- openclaw-memory-promotion:memory:memory/2026-04-14.md:158:160 -->
- - Candidate: Possible Lasting Truths: - Candidate: Assistant: ## 当前已安装技能 | 技能 | 路径 | 功能 | |------|------|------| | **self-improvement** | `~/.openclaw/skills/self-improvement` | 记录 learnings/errors/feature requests | | **ontology** | `~/.openclaw/skills/oswalpalash/ontology` | 知识图谱、结构化记忆 | | - confidence: 0.00 - evidence: memory/2026-04-14.md:138-140 [score=0.848 recalls=0 avg=0.620 source=memory/2026-04-14.md:13-15]

## Promoted From Short-Term Memory (2026-04-21)

