# AI Agent 项目作品集

> 这个仓库记录了我独立完成的 Agent 项目，这里是项目1-购票小助手

---

## 📦 项目一：购票小助手

### 项目背景
12306 查询流程繁琐，用户需要多次筛选日期、车站、车次。我尝试用 MCP 协议 + Cherry Studio，打造一个「对话即服务」的出行助手。

### 技术方案
- **客户端**：Cherry Studio（支持 MCP 协议）
- **MCP 服务器**：12306-mcp、amap-mcp、sequential-thinking
- **模型底座**：DeepSeek API + Ollama 本地模型

### MCP 配置代码
```json
{
  "mcpServers": {
    "12306-mcp": {
      "command": "npx",
      "args": ["-y", "12306-mcp"]
    },
    "amap-mcp": {
      "command": "npx",
      "args": ["-y", "@amap/amap-maps-mcp-server"],
      "env": {
        "AMAP_MAPS_API_KEY": "需自行申请高德API Key"
      }
    },
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}
