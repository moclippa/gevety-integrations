# Gevety Integrations

Connect your [Gevety](https://gevety.com) health data to AI assistants.

Gevety is a self-hosted blood test tracking platform with AI-powered biomarker analysis. These integrations let you query your health data directly from your favorite AI tools.

## Available Integrations

| Integration | Description | Install |
|-------------|-------------|---------|
| [Clawdbot](./clawdbot/) | Skill for Clawdbot AI assistant | `clawdhub install gevety` |
| [Claude Desktop](./claude-desktop/) | MCP server for Claude Desktop | `pip install gevety-mcp` |

## Quick Start

1. **Get a Gevety account** at [gevety.com](https://gevety.com)
2. **Upload your blood tests** to have biomarker data
3. **Generate an API token** at Settings → Developer API
4. **Choose your integration** and follow the setup guide

## What You Can Do

Once connected, you can ask your AI assistant:

- "What were my cholesterol levels in my last blood test?"
- "How has my vitamin D changed over the past year?"
- "What's my biological age?"
- "What should I focus on to improve my health?"
- "What tests am I due for?"

## API Endpoints

All integrations access the same 11 API endpoints:

| Endpoint | Description |
|----------|-------------|
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

## Privacy & Security

- Your health data stays private
- API tokens only grant access to your own data
- Neither AI assistants nor their providers store your health information
- Revoke tokens anytime at [gevety.com/settings](https://gevety.com/settings)

## Links

- **Website**: [gevety.com](https://gevety.com)
- **MCP Package**: [pypi.org/project/gevety-mcp](https://pypi.org/project/gevety-mcp/)

## License

MIT
