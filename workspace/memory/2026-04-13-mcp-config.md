# Session: 2026-04-13 05:44:53 UTC

- **Session Key**: agent:main:wecom:direct:6050991971899820576
- **Session ID**: bf06c2a3-043b-4344-bf60-3c02beb0bd0b
- **Source**: wecom

## Conversation Summary

user: Conversation info (untrusted metadata):
```json
{
  "message_id": "f4043d21e86682e34ae8018d8310110c",
  "sender_id": "6050991971899820576",
  "sender": "6050991971899820576",
  "timestamp": "Mon 2026-04-13 10:56 GMT+8"
}
```

Sender (untrusted metadata):
```json
{
  "label": "6050991971899820576",
  "id": "6050991971899820576"
}
```

在吗
assistant: 在的 🦞 正在处理定时任务配置，稍等一下。

刚才遇到 gateway 配对问题，正在重启：


assistant: 定时任务已添加。不过目前企业微信 MCP 接口有点问题（需要检查企业微信应用权限配置）。

让我检查一下当前定时任务状态：

assistant: ✅ **定时任务已创建完成！**

- **任务名称：** AI资讯推送
- **执行时间：** 每天早上 9:00
- **推送群：** wrwkcNBgAAHK_Fpq4bXBmDPQrRsEm6Yg

---

⚠️ **但有一个问题需要解决：**

目前企业微信 MCP 工具报错 `unsupported mcp biz type`，这意味着企业微信应用可能缺少调用 API 的权限。需要你检查：

1. **企业微信后台** → 应用管理 → 你的 AI Bot 应用
2. 查看 **API 权限** 是否开通了：
   - 发消息到群聊
   - 查看聊天记录
   - 通讯录权限

你可以在企业微信后台看看这个应用的权限配置，或者提供一下 `corpId`（企业ID），我帮你检查一下配置。

另外，任务触发后我需要先爬取新闻内容再发送，能否先测试一下推送功能是否正常？
user: Conversation info (untrusted metadata):
```json
{
  "message_id": "8ef174a1ee9c061bbe7a4f2a7cf86864",
  "sender_id": "6050991971899820576",
  "sender": "6050991971899820576",
  "timestamp": "Mon 2026-04-13 10:59 GMT+8"
}
```

Sender (untrusted metadata):
```json
{
  "label": "6050991971899820576",
  "id": "6050991971899820576"
}
```

测试
assistant: message 工具也报配对错误。让我换个方式试试：

assistant: MCP 接口仍然报错 `unsupported mcp biz type`。这是企业微信应用配置问题。

让我检查一下你的企业微信应用配置：


user: Conversation info (untrusted metadata):
```json
{
  "message_id": "9ad840473d8b287fe07d9b2612d23040",
  "sender_id": "6050991971899820576",
  "sender": "6050991971899820576",
  "timestamp": "Mon 2026-04-13 11:12 GMT+8"
}
```

Sender (untrusted metadata):
```json
{
  "label": "6050991971899820576",
  "id": "6050991971899820576"
}
```

好了吗
assistant: MCP 还是报错。这个错误是企业微信应用 API 权限问题，不是配置问题。

让我检查一下你的应用类型和权限：


assistant: 根据文档说明，定时推送功能需要配置 **Agent 模式**（需要 corpId、corpSecret、agentId）。

当前配置只有 Bot 模式（botId + secret），无法通过 MCP 发送消息。

---

**需要你提供以下信息来配置 Agent 模式：**

1. **CorpID**（企业ID）- 在企业微信后台「我的企业」→「企业信息」里可以找到
2. **CorpSecret** - 应用详情里的「Secret」
3. **AgentId** - 应用详情里的「AgentId」

或者你可以直接在企业微信后台 → 应用管理 → 你的AI应用 → 查看「API权限」看看有没有开通发消息相关权限。

---

另外，message 工具也报配对错误，让我检查一下：



assistant: WebSocket 已连接！消息发送走的是 WebSocket 通道。让我再试一次：


assistant: 根据日志分析：

**当前状态：**
1. ✅ WebSocket 连接正常
2. ✅ MCP 消息成功发送到企业微信 WebSocket 通道
3. ❌ 企业微信服务端返回错误码 846610：`unsupported mcp biz type`（API权限问题）

---

**问题根源：**

你的 AI Bot 应用（智能体）没有开通**群聊发消息**的 API 权限。企业微信的智能体（Bot） WebSocket 方式和 MCP API 是两套不同的接口。

**解决方案（二选一）：**

**方案1：配置 Agent 模式（推荐）**
需要提供：
- CorpID（企业ID）
- CorpSecret（应用Secret）
- AgentId（应用AgentId）

**方案2：开通智能体 API 权限**
在企业微信后台 → 应用管理 → 你的AI应用 → API权限 → 开通「发送应用消息」权限

---

你能提供一下 CorpID 和 AgentId 吗？或者先去企业微信后台看看应用的 API 权限状态？
user: Conversation info (untrusted metadata):
```json
{
  "message_id": "a19c63264f20b788ddb4d8419964b10c",
  "sender_id": "6050991971899820576",
  "sender": "6050991971899820576",
  "timestamp": "Mon 2026-04-13 11:16 GMT+8"
}
```

Sender (untrusted metadata):
```json
{
  "label": "6050991971899820576",
  "id": "6050991971899820576"
}
```

企业ID
ww853e50c7367c1f33
Bot ID
aibQ8L2GZVXgBerOHMvufmzHheHV5Uf-4WB
Secret
GBOlBzDkWzVMeaCFE5CFEcCUhCrs5x6iSKQNj7NQQu2
user: Conversation info (untrusted metadata):
```json
{
  "message_id": "24fe9ffa63f4ed1f5a08b7d35593e607",
  "sender_id": "6050991971899820576",
  "sender": "6050991971899820576",
  "timestamp": "Mon 2026-04-13 13:44 GMT+8"
}
```

Sender (untrusted metadata):
```json
{
  "label": "6050991971899820576",
  "id": "6050991971899820576"
}
```

在吗
assistant: 在的 🦞

让我检查一下之前配置的定时任务和企业微信推送状态：

