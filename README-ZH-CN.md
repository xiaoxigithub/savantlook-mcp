# 🔍 SavantLook MCP 服务器

一个模型上下文协议 (MCP) 服务器实现，提供访问 SavantLook API 数据的工具。

## 🌟 功能特性

SavantLook MCP 服务器提供以下工具：

- **域名分析** 📊
  - 域名概览信息
  - 自然搜索和付费搜索关键词分析
  - 竞争对手分析
  - 流量趋势和参与度指标
  - 反向链接分析

- **关键词分析** 🔑
  - 关键词概览数据
  - 相关关键词发现
  - 短语问题发现
  - 关键词难度和搜索量、意图、趋势、CPC 等数据
  - 魔法关键词挖掘工具

- **反向链接分析** 🔗
  - 反向链接数据
  - 引用域名分析
  - 反向链接概览和列表
  - 包括页面权重、内部链接、外部链接数量、页面链接、标题、来源 IP 等

- **账户管理** 👤
  - 账户详情和信用余额
  - API 使用统计

- **流量分析** 🚦
  - 域名流量摘要
  - 流量来源分析

## ⚙️ 设置

1. 使用我们的[关键词研究工具](https://www.savantlook.com/register)注册账户

2. 创建令牌
https://www.savantlook.com/user/api-tokens

3. 服务器配置
```json
  {
      "mcpServers": {
          "savantlook-mcp": {
              "url": "https://www.savantlook.com/mcp",
              "headers": {
                  "Authorization": "Bearer xxxxx",
                  "Content-Type": "application/json"
              }
          }
      }
  }
```


## 📋 变量

| 变量 | 描述 | 默认值 |
|----------|-------------|---------|
| `Authorization` | 您的 Savantlook API 密钥 | (必填) |


## 🛠️ 可用工具

| 工具名称 | 描述 | 必需参数 |
|-----------|-------------|---------------------|
| `account-details` | 获取当前用户账户信息和信用余额 | 无 |
| `adwords-competitors-list` | 付费搜索中的竞争对手 | target, target_type |
| `backlinks-list` | 获取特定域名或 URL 的反向链接列表 | target, target_type, display_number |
| `backlinks-overview` | 获取域名反向链接概览数据 | target, target_type |
| `organic-competitors-list` | 自然搜索竞争对手列表 | target, target_type, database, display_number, display_size |
| `domain-country-overview` | 获取域名在各国的流量数据，包括付费流量、自然流量、品牌流量等 | target, target_type |
| `domain-overview` | 获取域名概览 [权威性、反向链接数量、健康评分等] | target, target_type |
| `domain-trend` | 获取域名在指定时间段内的自然搜索、付费搜索、意图、流量和排名趋势 | target, target_type, database |
| `analytics-engagement` | 获取域名分析参与度指标（访问时长、跳出率、平均停留时间） | target, target_type |
| `get-databases` | 获取所有可用的区域数据库类型 | 无 |
| `domain-organic-keyword` | 域名自然搜索关键词 | target, target_type |
| `today-stats` | 获取用户今日 API 使用统计 | 无 |
| `magic-keywords` | 魔法关键词工具 - 精确关键词挖掘助手 | phrase, database, mode, display_number, display_size |


## 💰 API 单位消耗

SavantLook 的 API 请求会消耗您账户中的 API 单位。不同类型的请求消耗不同的单位数。您可以使用 `account-details` 工具查看您的 API 单位余额。

### ⚡ 限时优惠！⚡
现在是限时活动，测试阶段**全部只需2积分**。

### 关键词报告 API 单位消耗

| Tool | API Units per Line |
|------|-------------------|
| `today-stats` | 0 |
| `account-details` | 0 |
| `get-databases` | 0 |
| `analytics-engagement` | 0 |
| `domain-overview` | ~~4~~ 🔥 **2** |
| `backlinks-overview` | ~~4~~ 🔥 **2** |
| `domain-trend` | ~~5~~ 🔥 **2** |
| `domain-country-overview` | ~~5~~ 🔥 **2** |
| `domain-organic-keyword` | ~~10~~ 🔥 **2** |
| `adwords-competitors-list` | ~~10~~ 🔥 **2** |
| `organic-competitors-list` | ~~10~~ 🔥 **2** |
| `backlinks-list` | ~~10~~ 🔥 **2** |
| `magic-keywords` | ~~10~~ 🔥 **2** |

## 🖥️ 添加到 Cursor 或 Claude

将此 MCP 服务器添加到 Cursor 或 Claude：

### Cursor

1. 在 Cursor 中，转到设置 > MCP 服务器
2. 点击"添加服务器"
3. 使用以下设置配置服务器：
   - **名称**: `Savantlook MCP` (或您喜欢的任何名称)
   - **类型**: `streamable_http`
   - **变量**:
     - `Authorization`: 您的 Savantlook API 密钥
     - 其他可选变量
4. 点击"保存"


通过以下格式将此 MCP 添加到您的 MCP 服务器 JSON 配置文件中：

```json
{
    "mcpServers": {
        "savantlook-mcp": {
            "url": "https://www.savantlook.com/mcp",
            "headers": {
                "Authorization": "Bearer xxxxx",
                "Content-Type": "application/json"
            }
        }
    }
}
```


## 🔐 安全说明

- 切勿公开分享您的 Savantlook API 密钥
- API 密钥可访问您的 API 单位余额
- 泄露凭证可能导致未经授权的 API 使用和意外费用

## 📄 许可证

[MIT](./LICENSE)
