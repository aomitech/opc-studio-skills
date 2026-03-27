---
name: opcstudio-send-login-code
description: Call opcstudio-mcp-server send_login_code to send SMS OTP for login. Use when user asks for 验证码登录, 发送登录验证码, 或需要先获取短信验证码.
---

# OPCStudio Finance Send Login Code

## 适用场景

当用户需要短信验证码登录，且尚未发送验证码时使用本技能。

## MCP 服务器与工具

- Server: `opcstudio-mcp-server`
- Tool: `send_login_code`

## 工具输入规范

### `send_login_code`
- `phone` (string, required): 手机号

## 推荐工作流

1. 确认用户提供了手机号。
2. 调用 `send_login_code`。
3. 提示用户查看短信并提供验证码，以便下一步调用 `login_with_code`。

## 执行准则

- 若手机号缺失或格式明显异常，先让用户确认手机号。
- 失败时返回错误信息，并给出下一步（重试或确认手机号）。

## 对话模板

- “我先帮你发送登录验证码到该手机号，请收到后把验证码发给我。”
