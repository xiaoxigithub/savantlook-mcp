# 🔍 SavantLook MCP 服务器

一个实现模型上下文协议（MCP）的服务器，用于访问 SavantLook API 数据。

## 🌟 功能

SavantLook MCP 服务器提供以下工具：

- **域名分析** 📊
  - 域名概览信息
  - 自然搜索和付费搜索关键词分析
  - 竞争对手分析
  - 流量趋势和用户参与度指标

- **关键词分析** 🔑
  - 关键词概览数据
  - 相关关键词发现
  - 短语问题发现
  - 关键词难度、搜索量、意图、趋势、CPC 等数据
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

2. 创建 API 令牌
   [https://www.savantlook.com/user/api-tokens](https://www.savantlook.com/user/api-tokens)

3. 服务器配置
   ```json
   {
       "mcpServers": {
           "savantlook": {
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
|------|------|--------|
| `Authorization` | 您的 SavantLook API 密钥 | （必填） |

## 🛠️ 可用工具

| 工具名称 | 描述 | 必填参数 |
|----------|------|----------|
| `account-details` | 获取当前用户账户信息和信用余额 | 无 |
| `adwords-competitors-list` | 付费搜索中的竞争对手 | target, target_type |
| `backlinks-list` | 获取指定域名或 URL 的反向链接列表 | target, target_type, display_number |
| `backlinks-overview` | 获取域名反向链接概览数据 | target, target_type |
| `organic-competitors-list` | 自然搜索中的竞争对手列表 | target, target_type, database, display_number, display_size |
| `domain-country-overview` | 获取域名在各国家的流量数据，包括付费流量、自然流量、品牌流量等 | target, target_type |
| `domain-overview` | 获取域名概览（权威性、反向链接数、健康评分等） | target, target_type |
| `domain-trend` | 获取域名在指定时间段内的自然搜索、付费搜索、意图、流量和排名趋势 | target, target_type, database |
| `analytics-engagement` | 获取域名分析的用户参与度指标（访问时长、跳出率、平均停留时间） | target, target_type |
| `get-databases` | 获取按地区划分的可用数据库类型 | 无 |
| `domain-organic-keyword` | 域名自然搜索关键词 | target, target_type |
| `today-stats` | 获取用户当天的 API 使用统计 | 无 |
| `magic-keywords` | 魔法关键词工具 - 精准关键词挖掘助手 | phrase, database, mode, display_number, display_size |

## 💰 API 单位消耗

SavantLook 的 API 请求会消耗账户中的 API 单位。不同类型的请求消耗不同，您可以使用 `account-details` 工具检查 API 单位余额。

### ⚡ 限时优惠！ ⚡
当前为测试阶段限时活动，每行请求**仅需 2 个单位**。

### 关键词报告 API 单位消耗

| 工具 | 每行 API 单位 |
|------|--------------|
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

### Claude 示例（使用 Bearer 令牌）

```bash
claude mcp add --transport http savantlook https://www.savantlook.com/mcp \
  --header "Authorization: Bearer your-token"
```

### Cursor

1. 在 Cursor 中，进入 设置 > MCP 服务器
2. 点击“添加服务器”
3. 使用以下设置配置服务器：
   - **名称**：`Savantlook`（或您喜欢的名称）
   - **类型**：`streamable_http`
   - **变量**：
     - `Authorization`：您的 SavantLook API 密钥
     - 其他可选变量按需配置
4. 点击“保存”

## 🔐 安全须知

- 请勿公开分享您的 SavantLook API 密钥
- API 密钥可访问您的 API 单位余额
- 泄露凭证可能导致未经授权的 API 使用和意外费用

## 📚 最佳实践

以下是通过组合使用 SavantLook MCP 工具进行 SEO 分析的最佳实践示例，适合 SEO 专家、内容营销人员和开发人员。这些示例展示了如何通过命令分析网站表现、优化关键词策略和监控 API 使用。

### 1. 全面分析网站 SEO 表现
**目标**：评估网站（例如 `example.com`）的 SEO 表现，制定优化策略。
- **步骤**：
  1. 使用 `domain-overview` 获取域名权威性和流量概况：
     ```bash
     savantlook domain-overview example.com domain
     ```
  2. 使用 `domain-trend` 分析过去 6 个月的流量趋势（美国数据库）：
     ```bash
     savantlook domain-trend example.com domain us
     ```
  3. 使用 `analytics-engagement` 检查用户参与度指标（例如跳出率）：
     ```bash
     savantlook analytics-engagement example.com domain
     ```
  4. 使用 `organic-competitors-list` 识别自然搜索竞争对手：
     ```bash
     savantlook organic-competitors-list example.com domain us 5 large
     ```
- **用途**：生成综合 SEO 报告，识别流量增长点和用户体验问题，并与竞争对手进行比较。

### 2. 优化关键词策略
**目标**：为 `example.com` 的博客挖掘高潜力关键词，提升自然搜索流量。
- **步骤**：
  1. 使用 `get-databases` 确认目标市场数据库：
     ```bash
     savantlook get-databases
     ```
  2. 使用 `magic-keywords` 挖掘“digital marketing”相关关键词：
     ```bash
     savantlook magic-keywords "digital marketing" us related 10 large
     ```
  3. 使用 `domain-organic-keyword` 检查现有排名关键词：
     ```bash
     savantlook domain-organic-keyword example.com domain
     ```
- **用途**：制定内容计划，优化高潜力长尾关键词，提升排名靠前的关键词至前 3。

### 3. 反向链接策略优化
**目标**：分析 `example.com` 的反向链接质量，寻找新的链接机会。
- **步骤**：
  1. 使用 `backlinks-overview` 获取反向链接概况：
     ```bash
     savantlook backlinks-overview example.com domain
     ```
  2. 使用 `backlinks-list` 获取具体链接详情（前 20 个）：
     ```bash
     savantlook backlinks-list example.com domain 20
     ```
  3. 使用 `organic-competitors-list` 找到竞争对手，分析其链接：
     ```bash
     savantlook organic-competitors-list example.com domain us 3 large
     savantlook backlinks-overview competitor1.com domain
     ```
- **用途**：制定链接建设计划，清理低质量链接，联系高权威网站获取链接。

### 4. 监控和优化 API 使用
**目标**：管理多个网站的分析任务，确保不超出 API 配额。
- **步骤**：
  1. 使用 `account-details` 检查信用余额：
     ```bash
     savantlook account-details
     ```
  2. 使用 `today-stats` 监控每日 API 使用：
     ```bash
     savantlook today-stats
     ```
  3. 批量分析多个网站：
     ```bash
     for domain in example.com example2.com; do
         savantlook domain-overview $domain domain
         savantlook magic-keywords "digital marketing" us related 5 large
     done
     ```
- **用途**：优化 API 配额分配，自动化批量数据收集。

### 5. 综合竞品分析与关键词优化
**目标**：分析竞争对手的关键词和流量来源，优化 `example.com` 的策略。
- **步骤**：
  1. 使用 `organic-competitors-list` 和 `adwords-competitors-list` 分析竞争对手：
     ```bash
     savantlook organic-competitors-list example.com domain us 5 large
     savantlook adwords-competitors-list example.com domain
     ```
  2. 使用 `magic-keywords` 挖掘未被竞争对手覆盖的关键词：
     ```bash
     savantlook magic-keywords "seo software" us related 10 large
     ```
  3. 使用 `domain-country-overview` 优化区域性策略：
     ```bash
     savantlook domain-country-overview example.com domain
     ```
- **用途**：抢占竞争对手市场份额，优化区域性关键词和广告投放。

### 最佳实践总结
- **模块化分析**：将域名、关键词和竞争对手分析分步骤执行，整合结果生成报告。
- **自动化脚本**：编写脚本批量调用工具，保存结果到数据库或 CSV 文件。
- **定期监控**：每周运行 `account-details` 和 `today-stats`，跟踪数据变化。
- **跨工具整合**：结合 `magic-keywords` 和 `domain-organic-keyword`，优先优化高潜力关键词。

## 📄 许可证

[MIT](./LICENSE)