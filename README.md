# SavantLook MCP Server

A Model Context Protocol (MCP) server implementation that provides tools for accessing SavantLook API data.

## Features

The SavantLook MCP server provides tools for:

- **Domain Analytics**
  - Domain overview information
  - Organic and paid keywords analysis
  - Competitor analysis
  - Traffic trends and engagement metrics
  - Backlink analysis

- **Keyword Analytics**
  - Keyword overview data
  - Related keyword discovery
  - Keyword difficulty and search volume
  - Magic keyword mining tool

- **Backlink Analysis**
  - Backlink data
  - Referring domains analysis
  - Backlink overview and lists

- **Account Management**
  - Account details and credit balance
  - API usage statistics

- **Traffic Analytics**
  - Traffic summary for domains
  - Traffic sources analysis
  - (Note: Requires .Trends API subscription)

## Setup

1. Register an account using our [keyword research tool](https://www.savantlook.com/register)

2. Create a token
https://www.savantlook.com/user/api-tokens

3. Server Config
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


## Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `Authorization` | Your Savantlook API key | (Required) |


## Available Tools

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

Parameters in [brackets] are optional.

## API Units Consumption

API requests to SavantLook consume API units from your account. Different types of requests have different costs. You can check your API units balance using the `account-details` tool.

Now it is a limited time event, <span style="color:red; font-weight:bold">only 2 points</span> are required during the operation test phase.

### Keyword Reports API Units Consumption

| Tool | API Units per Line |
|------|-------------------|
| `today-stats` | 0 |
| `account-details` | 0 |
| `get-databases` | 0 |
| `analytics-engagement` | 0 |
| `domain-overview` | ~~<span style="color:red">4</span>~~ 2 |
| `backlinks-overview` | ~~<span style="color:red">4</span>~~ 2 |
| `domain-trend` | ~~<span style="color:red">5</span>~~ 2 |
| `domain-country-overview` | ~~<span style="color:red">5</span>~~ 2 |
| `domain-organic-keyword` | ~~<span style="color:red">10</span>~~ 2 |
| `adwords-competitors-list` | ~~<span style="color:red">10</span>~~ 2 |
| `organic-competitors-list` | ~~<span style="color:red">10</span>~~ 2 |
| `backlinks-list` | ~~<span style="color:red">10</span>~~ 2 |
| `magic-keywords` | ~~<span style="color:red">10</span>~~ 2 |

## Adding to Cursor or Claude

To add this MCP server to Cursor or Claude:

### Cursor

1. In Cursor, go to Settings > MCP Servers
2. Click "Add Server"
3. Configure the server with the following settings:
   - **Name**: `Savantlook MCP` (or any name you prefer)
   - **Type**: `streamable_http`
   - **Variables**:
     - `Authorization`: Your Savantlook API key
     - Other optional variables as needed
4. Click "Save"


Configure your MCP servers JSON file for your designated consuming environment by adding this MCP using the following format:

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


## Security Notes

- Never share your Savantlook API key publicly
- API key provides access to your API units balance
- Exposing credentials can lead to unauthorized API usage and unexpected charges

## License

[MIT](./LICENSE)
