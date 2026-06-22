# Goodtake Skills

AI image generation skills for Claude Code, Cursor, Codex, and other AI coding agents.

## Install

```bash
npx skills add goodtake-ai/skills
```

This installs all Goodtake skills into your active agent. Restart the agent to pick up the new skills.

## Skills

| Skill | Invoke | Description |
|---|---|---|
| `goodtake-generate` | `/goodtake:generate` | Generate images via the Goodtake CLI |

## Prerequisites

1. Install the Goodtake CLI:
   ```bash
   npm install -g @goodtake/cli
   ```

2. Authenticate:
   ```bash
   gt auth login
   ```

## Usage

After installing, just ask your agent naturally:

> "Generate an image of a futuristic city at night"

> "Create a product shot of white sneakers on a marble surface, 1:1 aspect ratio"

> "Use goodtake to make a 16:9 hero banner with abstract gradients"

The agent will invoke `gt generate image` and return the downloaded path or URL.

## MCP connector

Alternatively, add Goodtake as an MCP connector in Claude Settings:

1. Open Claude → Settings → Connectors
2. Add URL: `https://mcp.goodtake.ai/mcp`
3. Click Connect and sign in

## Links

- [goodtake.ai/cli](https://goodtake.ai/cli) — full documentation
- [github.com/goodtake-ai/skills](https://github.com/goodtake-ai/skills)
