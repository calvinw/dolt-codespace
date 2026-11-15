# Instructions for the coding agent

The user is a student learning Dolt (a SQL database with Git-style versioning)
and DoltHub. You run the commands for them in this codespace. Explain briefly
what each command does and show its output, so they learn the workflow.

## Installing Dolt

If `dolt version` fails, install it (the codespace user has passwordless sudo):

```bash
sudo bash -c 'curl -L https://github.com/dolthub/dolt/releases/latest/download/install.sh | bash'
dolt version
```

Before any commit or login, set the user's name and DoltHub email. Ask for
them if you don't have them:

```bash
dolt config --global --add user.name "NAME"
dolt config --global --add user.email "EMAIL"
```

## Logging in to DoltHub

Do NOT run `dolt login`. It waits for the browser and your command will time
out. Instead:

1. Make a new key: `dolt creds new`. It prints a public key.
2. Give the user this link, with the public key at the end, and tell them to
   open it while signed in to DoltHub, type a description such as
   `codespace`, and click **Create**:
   `https://www.dolthub.com/settings/credentials#PUBLIC_KEY`
   If the key is not filled in on that page, tell them to paste the public
   key into it.
3. Wait for the user to say they have done it.
4. Select the key and check it: `dolt creds use PUBLIC_KEY`, then
   `dolt creds check`. It should report the user's DoltHub username. If it
   fails, the key was not added yet: ask them to try the link again.

## Working with a database

- Keep Dolt databases in the home folder (for example `~/retail-orders`),
  not inside this git repository, so they are never committed to git.
- Run SQL with `dolt sql -q "..."`, or load a file with
  `dolt sql < FILE.sql`. Don't open the interactive `dolt sql` shell; it
  waits for input.
- Before committing, show `dolt status` and `dolt diff` so the user sees what
  changed.
- Commit with `dolt add .` and `dolt commit -m "..."`, using a message that
  says what changed.

## Creating a database from a SQL file (retail-orders/)

1. `mkdir ~/retail-orders && cd ~/retail-orders && dolt init`
2. `dolt sql < /path/to/this/repo/retail-orders/retail-orders.sql`
3. Show the tables and row counts, then `dolt add .` and
   `dolt commit -m "Create retail orders database"`.

## Pushing to DoltHub

- `dolt push` cannot create a database on DoltHub. The user first creates an
  empty database on the DoltHub website. If they haven't, tell them to do
  that, then wait.
- Push only to the user's own DoltHub account, never to `calvinw/...`:
  `dolt remote add origin USERNAME/retail-orders`, then
  `dolt push -u origin main` the first time and `dolt push` after that.
- If the push says permission denied, the login is missing or the database
  belongs to someone else: check `dolt creds check` and the remote with
  `dolt remote -v`.
- After pushing, tell the user to refresh their database page on DoltHub.
- Don't use `--force`, don't delete tables or branches, and don't rewrite
  history unless the user asks.
