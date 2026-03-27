---
name: opcstudio-login-with-code
description: Call opcstudio-mcp-server login_with_code to establish authenticated session using phone and SMS OTP. Use when user provides 验证码 and needs to complete login before protected finance tools.
---

# OPCStudio Login With Code

## 适用场景

当用户已拿到短信验证码，需要完成登录会话时使用本技能。

## MCP 服务器与工具

- Server: `opcstudio-mcp-server`
- Tool: `login_with_code`

## 工具输入规范

### `login_with_code`
- `phone` (string, required): 手机号
- `code` (string, required): 短信验证码

## 推荐工作流

1. 确认 `phone` 与 `code` 都已提供。
2. 调用 `login_with_code`。
3. 若登录成功，告知用户可继续调用受保护工具（如 `invoice_upload`）。

## 执行准则

- 验证码为空或明显无效时，先要求用户重新提供。
- 登录失败时，优先建议“重新发送验证码并重试登录”。

## 对话模板

- “我现在用手机号和验证码为你登录，成功后就可以继续调用发票上传等需要登录的工具。”
