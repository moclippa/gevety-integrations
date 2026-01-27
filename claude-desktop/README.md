# Gevety MCP Server for Claude Desktop

Connect Claude Desktop to your Gevety health data using the Model Context Protocol (MCP).

## Installation

```bash
pip install gevety-mcp
```

Or with uvx:
```bash
uvx gevety-mcp
```

## Setup

### 1. Generate an API Token

1. Go to [gevety.com/settings](https://gevety.com/settings)
2. Click "Developer API" tab
3. Click "Generate Token"
4. Copy the token (starts with `gvt_`)

### 2. Configure Claude Desktop

Open your Claude Desktop config file:

- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

Add the Gevety server:

```json
{
  "mcpServers": {
    "gevety": {
      "command": "gevety-mcp",
      "env": {
        "GEVETY_API_TOKEN": "gvt_your_token_here"
      }
    }
  }
}
```

### 3. Restart Claude Desktop

Quit and reopen Claude Desktop to load the configuration.

### 4. Start Asking Questions

You'll see "gevety" in Claude's available tools. Try:

- "What were my cholesterol levels?"
- "How has my vitamin D changed over the past year?"
- "What's my biological age?"
- "What should I focus on for my health?"

## Available Tools

The MCP server provides 11 tools:

| Tool | Description |
|------|-------------|
| `list_available_data` | Discover what health data exists |
| `get_health_summary` | Overall health scores and status |
| `query_biomarker` | Detailed biomarker history and trends |
| `get_wearable_stats` | Daily metrics from connected wearables |
| `get_opportunities` | Ranked health improvement opportunities |
| `get_biological_age` | Biological age calculation |
| `list_supplements` | Current supplement stack |
| `get_activities` | Workout history from wearables |
| `get_today_actions` | Daily action checklist |
| `get_protocol` | 90-day health protocol priorities |
| `get_upcoming_tests` | Tests due or recommended |

## Troubleshooting

**Token not working?**
- Check expiry date at gevety.com/settings
- Generate a new token if needed

**MCP server not appearing?**
- Verify config file path is correct
- Ensure JSON is valid (no trailing commas)
- Restart Claude Desktop after changes

**Getting rate limited?**
- Wait a few minutes before retrying
- Rate limits prevent abuse

## Privacy

- Your health data stays private
- Claude and Anthropic do not store your health information
- Revoke tokens anytime at gevety.com/settings

## Links

- [PyPI Package](https://pypi.org/project/gevety-mcp/)
- [Gevety Website](https://gevety.com)
- [API Documentation](https://api.gevety.com/api/v1/docs)
