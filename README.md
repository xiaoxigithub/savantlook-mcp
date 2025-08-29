# 🔍 SavantLook MCP Server

A Model Context Protocol (MCP) server implementation that provides tools for accessing SavantLook API data.

## 🌟 Features

The SavantLook MCP server provides tools for:

- **Domain Analytics** 📊
  - Domain overview information
  - Organic and paid keywords analysis
  - Competitor analysis
  - Traffic trends and engagement metrics

- **Keyword Analytics** 🔑
  - Keyword overview data
  - Related keyword discovery
  - Phrase questions discovery
  - Keyword difficulty, search volume, intents, trends, CPC data, etc.
  - Magic keyword mining tool

- **Backlink Analysis** 🔗
  - Backlink data
  - Referring domains analysis
  - Backlink overview and lists
  - Including page weight, internal links, number of external links, page links, titles, source IP, etc.

- **Account Management** 👤
  - Account details and credit balance
  - API usage statistics

- **Traffic Analytics** 🚦
  - Traffic summary for domains
  - Traffic sources analysis

## ⚙️ Setup

1. Register an account using our [keyword research tool](https://www.savantlook.com/register)

2. Create a token
   [https://www.savantlook.com/user/api-tokens](https://www.savantlook.com/user/api-tokens)

3. Server Config
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

## 📋 Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `Authorization` | Your Savantlook API key | (Required) |

## 🛠️ Available Tools

| Tool Name | Description | Required Parameters |
|-----------|-------------|---------------------|
| `account-details` | Retrieve current user account information and credit balance | None |
| `adwords-competitors-list` | Competitors in Paid Search | target, target_type |
| `backlinks-list` | Get backlinks list for a specific domain or URL | target, target_type, display_number |
| `backlinks-overview` | Retrieve domain backlinks overview data | target, target_type |
| `organic-competitors-list` | Competitors in Organic Search List | target, target_type, database, display_number, display_size |
| `domain-country-overview` | Get domain traffic data for each country, including paid traffic, organic traffic, branded traffic, and more. | target, target_type |
| `domain-overview` | Retrieve domain overview [authority, backlink count, health score, etc.] | target, target_type |
| `domain-trend` | Retrieve a domain's organic search, paid search, intent, traffic, and ranking trends over a specified time period | target, target_type, database |
| `analytics-engagement` | Retrieve domain analytics engagement metrics (visit duration, bounce rate, average stay time) | target, target_type |
| `get-databases` | Get all available database types by region | None |
| `domain-organic-keyword` | Domain Organic Search Keywords | target, target_type |
| `today-stats` | Retrieve today's API usage statistics for the user | None |
| `magic-keywords` | Magic Keyword Tool - Precise Keyword Digging Assistant | phrase, database, mode, display_number, display_size |

## 💰 API Units Consumption

API requests to SavantLook consume API units from your account. Different types of requests have different costs. You can check your API units balance using the `account-details` tool.

### ⚡ Limited Time Offer! ⚡
Now it is a limited time event, **only 2 points** are required during the test phase.

### Keyword Reports API Units Consumption

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

## 🖥️ Adding to Cursor or Claude

### Claude Example with Bearer Token

```bash
claude mcp add --transport http savantlook https://www.savantlook.com/mcp \
  --header "Authorization: Bearer your-token"
```

### Cursor

1. In Cursor, go to Settings > MCP Servers
2. Click "Add Server"
3. Configure the server with the following settings:
   - **Name**: `Savantlook` (or any name you prefer)
   - **Type**: `streamable_http`
   - **Variables**:
     - `Authorization`: Your Savantlook API key
     - Other optional variables as needed
4. Click "Save"

## 🔐 Security Notes

- Never share your Savantlook API key publicly
- API key provides access to your API units balance
- Exposing credentials can lead to unauthorized API usage and unexpected charges

## 📚 Best Practices

The following best practice examples demonstrate how to combine SavantLook MCP tools to perform SEO analysis, suitable for SEO specialists, content marketers, and developers. These examples show how to use commands to analyze website performance, optimize keyword strategies, and monitor API usage.

### 1. Comprehensive Website SEO Analysis
**Goal**: Evaluate the SEO performance of a website (e.g., `example.com`) to develop an optimization strategy.
- **Steps**:
  1. Use `domain-overview` to retrieve domain authority and traffic overview:
     ```bash
     savantlook domain-overview example.com domain
     ```
  2. Use `domain-trend` to analyze traffic trends over the past 6 months (US database):
     ```bash
     savantlook domain-trend example.com domain us
     ```
  3. Use `analytics-engagement` to check user engagement metrics (e.g., bounce rate):
     ```bash
     savantlook analytics-engagement example.com domain
     ```
  4. Use `organic-competitors-list` to identify organic search competitors:
     ```bash
     savantlook organic-competitors-list example.com domain us 5 large
     ```
- **Use Case**: Generate a comprehensive SEO report, identify traffic growth opportunities, and address user experience issues by comparing with competitors.

### 2. Optimizing Keyword Strategy
**Goal**: Discover high-potential keywords for `example.com`’s blog to boost organic search traffic.
- **Steps**:
  1. Use `get-databases` to confirm available regional databases:
     ```bash
     savantlook get-databases
     ```
  2. Use `magic-keywords` to discover keywords related to “digital marketing”:
     ```bash
     savantlook magic-keywords "digital marketing" us related 10 large
     ```
  3. Use `domain-organic-keyword` to check existing ranked keywords:
     ```bash
     savantlook domain-organic-keyword example.com domain
     ```
- **Use Case**: Develop a content plan targeting high-potential long-tail keywords and optimize existing keywords to rank in the top 3.

### 3. Backlink Strategy Optimization
**Goal**: Analyze the backlink quality of `example.com` and identify new link-building opportunities.
- **Steps**:
  1. Use `backlinks-overview` to retrieve backlink summary:
     ```bash
     savantlook backlinks-overview example.com domain
     ```
  2. Use `backlinks-list` to get detailed backlink information (top 20):
     ```bash
     savantlook backlinks-list example.com domain 20
     ```
  3. Use `organic-competitors-list` to find competitors and analyze their backlinks:
     ```bash
     savantlook organic-competitors-list example.com domain us 3 large
     savantlook backlinks-overview competitor1.com domain
     ```
- **Use Case**: Develop a link-building strategy, remove low-quality links, and reach out to high-authority websites for new links.

### 4. Monitoring and Optimizing API Usage
**Goal**: Manage SEO analysis tasks for multiple websites while ensuring API quota is not exceeded.
- **Steps**:
  1. Use `account-details` to check credit balance:
     ```bash
     savantlook account-details
     ```
  2. Use `today-stats` to monitor daily API usage:
     ```bash
     savantlook today-stats
     ```
  3. Perform batch analysis for multiple websites:
     ```bash
     for domain in example.com example2.com; do
         savantlook domain-overview $domain domain
         savantlook magic-keywords "digital marketing" us related 5 large
     done
     ```
- **Use Case**: Optimize API quota allocation and automate bulk data collection for multiple websites.

### 5. Comprehensive Competitor Analysis and Keyword Optimization
**Goal**: Analyze competitors’ keywords and traffic sources for `example.com` to optimize its strategy.
- **Steps**:
  1. Use `organic-competitors-list` and `adwords-competitors-list` to analyze competitors:
     ```bash
     savantlook organic-competitors-list example.com domain us 5 large
     savantlook adwords-competitors-list example.com domain
     ```
  2. Use `magic-keywords` to discover untapped keywords:
     ```bash
     savantlook magic-keywords "seo software" us related 10 large
     ```
  3. Use `domain-country-overview` to optimize regional strategies:
     ```bash
     savantlook domain-country-overview example.com domain
     ```
- **Use Case**: Capture competitors’ market share and optimize regional keywords and ad campaigns.

### Best Practice Summary
- **Modular Analysis**: Break down domain, keyword, and competitor analysis into separate steps and combine results for comprehensive reports.
- **Automation Scripts**: Write scripts to batch-process tools, saving results to databases or CSV files.
- **Regular Monitoring**: Run `account-details` and `today-stats` weekly to track data changes and manage API usage.
- **Cross-Tool Integration**: Combine `magic-keywords` with `domain-organic-keyword` to prioritize high-potential keywords for optimization.

## 📄 License

[MIT](./LICENSE)