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
3. Click **Code → Codespaces → Create codespace on main** on this repo.

## Start OpenCode

1. In the terminal, type `opencode` and press **Enter**.
2. Type `/connect` and press **Enter**. Start typing `openrouter`, highlight
   **OpenRouter**, and press **Enter**.
3. Paste your OpenRouter API key (get one at <https://openrouter.ai/keys>) and
   press **Enter**.

OpenCode starts with **DeepSeek V4.1 Flash** on OpenRouter, set in
`opencode.json`. Use `/models` to switch models.

Treat your API key like a password: paste it only into OpenCode, never into a
file in the repository.

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
