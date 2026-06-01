# AI Agent 项目作品集

> 我是XXX，正在求职 AI Agent 产品经理。这个仓库记录了我独立完成的 Agent 项目。

---

## 📦 项目一：购票小助手

### 项目背景
12306 查询流程繁琐，用户需要多次筛选日期、车站、车次。我尝试用 MCP 协议 + Cherry Studio，打造一个「对话即服务」的出行助手。

### 核心能力
- **对话式火车票查询**：支持模糊日期解析（"明天""下周一"）、快捷指令"换一下"
- **多轮记忆与无票中转推荐**：记住上下文，无票时自动推荐中转方案或邻近日期
- **集成高德地图**：路线规划、周边POI搜索（酒店/餐厅）、天气查询

### 项目成果
- **查询效率**：较 12306 App 提升约 60%
- **交互体验**：平均交互轮次从 4.2 次降至 1.5 次
- **方法论沉淀**：提炼出工具调用 Agent 的评估框架，包含 3 个核心指标：
  - 意图识别准确率
  - 工具调用成功率
  - 端到端响应延迟

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
