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
4. Click **Code → Codespaces → Create codespace on main** on this repo.
5. When the codespace opens, the terminal asks for your OpenRouter key. Paste
   it and press Enter (nothing shows as you paste). It is saved in the
   codespace, not in the repo. If no question appears, open a new terminal
   with the **+** in the terminal panel.
6. Start OpenCode with `opencode` and pick an OpenRouter model with `/models`.

To use the key in all your codespaces without pasting it, save it instead as
a [Codespaces secret](https://github.com/settings/codespaces) named
`OPENROUTER_API_KEY` and give it access to this repo. To check the key is
there:

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
