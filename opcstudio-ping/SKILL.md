---
name: opcstudio-ping
description: Call opcstudio-mcp-server ping for MCP connectivity and health check. Use when user asks to test server availability, connectivity, or quick diagnostics before business tool calls.
---

# OPCStudio Finance Ping

## 适用场景

当用户需要快速验证 MCP 服务是否可用时使用本技能。

## MCP 服务器与工具

- Server: `opcstudio-mcp-server`
- Tool: `ping`

## 工具输入规范

### `ping`
- `message` (string, optional)

## 推荐工作流

1. 直接调用 `ping`（可带 `message`）。
2. 返回 `pong` 内容并解释服务连通状态。

## 执行准则

- 该工具只做健康检查，不等同于业务接口可用性验证。
- 若 `ping` 正常但业务接口失败，建议继续排查登录态或参数问题。

## 对话模板

- “我先做一次 MCP 连通性检查，确认服务端可达。”
