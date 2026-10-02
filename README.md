# Web Data API Plan Finder

MCP server that compares web scraping, crawling and SERP API plans against your workload and conditions: the monthly cost of each plan for your volume, and whether each condition (budget, concurrent requests, JavaScript rendering, premium proxies, country targeting, billing of failed requests) is met, not met or unknown. Every stated value matches the provider's official pricing and documentation as of the check date given with it.

No API key or sign-up. The tools only read the plan list.

Remote MCP server (Streamable HTTP): https://plans.intoperson.com/mcp

Official MCP registry name: `io.github.scraping-api-plans/web-data-plan-finder`

## Connect

### Claude Code

```shell
claude mcp add --transport http web-data-plan-finder https://plans.intoperson.com/mcp
```

### Claude (Pro and Max plans)

Customize > Connectors, click "+", then "Add custom connector", and paste this URL:

```text
https://plans.intoperson.com/mcp
```

### Codex CLI

```shell
codex mcp add web-data-plan-finder --url https://plans.intoperson.com/mcp
```

### Cursor (mcp.json)

```json
{
  "mcpServers": {
    "web-data-plan-finder": {
      "url": "https://plans.intoperson.com/mcp"
    }
  }
}
```

### VS Code (.vscode/mcp.json)

```json
{
  "servers": {
    "web-data-plan-finder": {
      "type": "http",
      "url": "https://plans.intoperson.com/mcp"
    }
  }
}
```

### Clients that only start local servers

```json
{
  "mcpServers": {
    "web-data-plan-finder": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://plans.intoperson.com/mcp"
      ]
    }
  }
}
```

## Tools

| Tool | What it does |
| --- | --- |
| `search` | Find web data API plans by conditions |
| `get_details` | Get recorded conditions of a plan or product |
| `check_conditions` | Check plans against conditions |
| `cost_scenarios` | Plan costs as the workload changes |
| `relax_conditions` | Smallest condition changes that admit plans |

Every tool is read-only. An unknown condition means the official pages do not state it; it is never guessed.

## More

- Guide (conditions, how monthly cost is worked out, REST API): https://plans.intoperson.com/guide
- How plans are collected and ordered: https://plans.intoperson.com/disclosure
- Privacy (what is recorded per request): https://plans.intoperson.com/privacy
