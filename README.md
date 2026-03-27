# Opc Studio Skills

### 使用方式

1. 配置mcp server
   在`mcp.json`文件中添加 `opcstudio-mcp-server`

```
{
  "mcpServers": {
    "opcstudio-mcp-server": {
      "url": "https://oneai.aomi.tech/api/v1/mcp",
    }
  }
}
```

2. 安装 skill
```
npx skills add https://github.com/aomitech/opc-studio-skills --skill "*"
```