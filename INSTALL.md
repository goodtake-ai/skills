# Installation

## Recommended: npx

```bash
npx skills add goodtake-ai/skills
```

Works with Claude Code, Cursor, and Codex. Restart your agent after installing.

## GitHub CLI

Requires [GitHub CLI](https://cli.github.com/) v2.90+:

```bash
gh skill install goodtake-ai/skills
```

## Claude Code marketplace

```
/plugin marketplace add goodtake-ai/skills
/plugin install goodtake@goodtake
```

## Manual (universal fallback)

```bash
git clone --depth 1 https://github.com/goodtake-ai/skills.git
cd skills && ./setup
```

## Prerequisites

1. Install the Goodtake CLI:
   ```bash
   npm install -g @goodtake/cli
   ```

2. Authenticate:
   ```bash
   gt auth login
   ```
