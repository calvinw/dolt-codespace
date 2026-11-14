# Dolt Codespace

A GitHub Codespace for working with [Dolt](https://www.dolthub.com), a SQL
database with Git-style versioning. You install Dolt yourself, log in to
DoltHub, then clone, change, commit and push a database you own.

The codespace also has three AI coding agents installed with `npm install -g`:

| Agent | npm package | Command |
|---|---|---|
| OpenCode | `@opencode/cli` | `opencode` |
| Codex | `@openai/codex` | `codex` |
| Claude Code | `@anthropic-ai/claude-code` | `claude` |

## Start it

Click **Code → Codespaces → Create codespace on main**.

## 1. Install Dolt

In the terminal:

```bash
sudo bash -c 'curl -L https://github.com/dolthub/dolt/releases/latest/download/install.sh | bash'
```

Check that it worked:

```bash
dolt version
```

## 2. Tell Dolt who you are

Use the email of your DoltHub account. Do this before logging in.

```bash
dolt config --global --add user.name "Your Name"
dolt config --global --add user.email "you@example.com"
```

## 3. Log in to DoltHub

Sign in to [dolthub.com](https://www.dolthub.com) in a browser tab first. Then:

```bash
dolt login
```

1. Dolt prints a link to the DoltHub **Credentials** page. Ctrl-click
   (Cmd-click on a Mac) it.
2. On that page, type a description such as `codespace` and click **Create**.
3. Go back to the terminal. After a few seconds it prints
   `Key successfully associated with user: ...`.

You stay logged in until you delete the codespace.

## 4. Fork, clone, commit, push

1. On DoltHub, open
   [calvinw/retail-orders](https://www.dolthub.com/repositories/calvinw/retail-orders)
   and click **Fork** to make your own copy.
2. Clone **your** fork:

   ```bash
   dolt clone YOUR-USERNAME/retail-orders
   cd retail-orders
   ```

3. Look at the data:

   ```bash
   dolt sql -q "SELECT * FROM products;"
   ```

4. Make a change, check it, and commit it:

   ```bash
   dolt sql -q "INSERT INTO customers (first_name, last_name, email) VALUES ('First', 'Last', 'me@example.com');"
   dolt diff
   dolt add .
   dolt commit -m "Add myself as a customer"
   ```

5. Push it to your fork on DoltHub:

   ```bash
   dolt push origin main
   ```

Refresh your fork on DoltHub to see your commit.
