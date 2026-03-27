name: opcstudio-finance-invoice-upload
description: Call opcstudio-mcp-server invoice_upload for invoice registration. Use when user mentions 发票上传, 发票登记, 上传发票文件. Try upload first; if response indicates login required, then guide user through send_login_code and login_with_code.
---

# OPCStudio Finance Invoice Upload

## 适用场景

当用户提到以下需求时使用本技能：
- 发票上传或登记
- 上传本地发票文件并调用登记接口

## MCP 服务器与工具

- Server: `opcstudio-mcp-server`
- Tool: `invoice_upload`

## 工具输入规范

### `invoice_upload`
- `filePath` (string, required): 本地文件绝对路径，支持常见发票文件类型（如 pdf/jpg/png/webp）

## 推荐工作流

按顺序执行：

1. 先直接调用 `invoice_upload`。
2. 若返回“请先登录账号”或明确的未登录提示，再进入登录流程：
   - 调用 `send_login_code`
   - 索取验证码后调用 `login_with_code`
3. 登录成功后，重新调用 `invoice_upload`。

## 执行准则

- 在调用工具前，先确认用户是否已提供必填参数。
- 首次上传失败且提示需登录时，再触发登录流程，不要预先要求登录。
- `filePath` 必须是绝对路径；如果用户给相对路径，先让用户确认完整路径。
- 工具返回 JSON 文本时，提炼关键信息给用户，同时保留原始关键字段。
- 如果接口失败，优先返回可执行下一步（重试、补参数、重新登录）。

## 对话模板

### 上传发票
- “请提供发票文件的本地绝对路径（例如 `/Users/name/Downloads/invoice.pdf`），我先尝试直接上传登记。”

### 需要登录时
- “接口提示当前会话未登录。我先发送验证码，登录后再自动重试上传。”
