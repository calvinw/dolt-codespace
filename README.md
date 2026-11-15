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
2. Click **Code → Codespaces → Create codespace on main** on this repo.

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

## Exercises

Each folder is one exercise, with its own directions in a `README-` file:

| Folder | What you do |
|---|---|
| [retail-orders](retail-orders/README-retail-orders.md) | The agent installs Dolt, logs you in to DoltHub, builds a retail orders database from `retail-orders.sql`, and pushes it to a new database on your DoltHub account. |
| [sales-csv-data](sales-csv-data/README-sales-csv-data.md) | Starting from one big `sales.csv` file, you and the agent design a database with three tables (stores, products and sales), build it in Dolt, and push it to DoltHub. |
| [excel-to-database](excel-to-database/README-excel-to-database.md) | Open an Excel workbook with two worksheets, find its problems, and with the agent turn it into a database whose keys keep those problems out. |
| [dolt-branches](dolt-branches/README-dolt-branches.md) | Build a small boutique database with three views, raise prices on a branch, compare what the views show on each branch, push the branch to DoltHub, and open a pull request for your manager to approve. |
| [company-analysis](company-analysis/README-company-analysis.md) | The agent analyzes an existing database, [calvinw/BusMgmtBenchmarks](https://www.dolthub.com/repositories/calvinw/BusMgmtBenchmarks), compares two retail companies in one year with charts, and builds a PowerPoint deck. |

The first time you use Dolt in a codespace, the agent has to install it and
log you in to DoltHub. The prompts for that are Steps 1 and 2 of
[retail-orders](retail-orders/README-retail-orders.md).
