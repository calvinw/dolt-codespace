# Dolt Codespace

A GitHub Codespace where an AI agent sets up [Dolt](https://www.dolthub.com),
a SQL database with Git-style versioning, and helps you clone, change, commit
and push a database you own on DoltHub.

The codespace has three AI coding agents installed with `npm install -g`:

| Agent | npm package | Command |
|---|---|---|
| OpenCode | `@opencode/cli` | `opencode` |
| Codex | `@openai/codex` | `codex` |
| Claude Code | `@anthropic-ai/claude-code` | `claude` |

`AGENTS.md` tells the agents how to install Dolt, log in to DoltHub and work
with the database, so your prompts can be short.

## Before you start

1. Make an account on [DoltHub](https://www.dolthub.com) and stay signed in.
2. Open
   [calvinw/retail-orders](https://www.dolthub.com/repositories/calvinw/retail-orders)
   and click **Fork**. This makes your own copy, which you can push to.
3. Get an OpenRouter API key at <https://openrouter.ai/keys>.
4. Save the key as a Codespaces secret: open
   <https://github.com/settings/codespaces>, click **New secret**, name it
   `OPENROUTER_API_KEY`, paste the key as the value, and under
   **Repository access** pick this repo. Click **Add secret**.
5. Click **Code → Codespaces → Create codespace on main** on this repo.
   (If a codespace was already running when you added the secret, restart it
   so it picks up the key.)
6. Start OpenCode with `opencode`. It finds your key, turns on OpenRouter, and
   starts with DeepSeek V4.1 Flash (set in `opencode.json`). Use `/models` to
   switch models.

To check the key reached the codespace, run this in the terminal:

```bash
test -n "$OPENROUTER_API_KEY" && echo "key is set" || echo "key is NOT set"
```

## Prompts to give the agent

Replace the parts in capitals with your own details.

```default
Install Dolt and set it up with my name YOUR NAME and my DoltHub email YOUR EMAIL.
```

```default
Log me in to DoltHub.
```

The agent gives you a link. Open it, type a description such as `codespace`,
click **Create**, then tell the agent you are done.

```default
Clone my fork YOUR-DOLTHUB-USERNAME/retail-orders and show me its tables and what is in them.
```

```default
Add me as a customer in the customers table. Show me what changed, commit it with a clear message, and push it to my fork.
```

Refresh your fork on DoltHub and open its commit history to see your commit.
