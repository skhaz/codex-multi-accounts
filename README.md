# cx

Show remaining Codex limits and switch accounts by email.
Requires `uv`, Python 3.14+, the Codex CLI, and macOS or Linux.

Run from the project folder to create the command link:

```sh
mkdir -p ~/.local/bin
ln -s "$PWD/cx.py" ~/.local/bin/cx
export PATH="$HOME/.local/bin:$PATH"
```

Add the `export` line to your shell configuration to keep it after a restart.

| Command | Action |
| --- | --- |
| `cx` | Show saved accounts and remaining limits. `*` marks the active account. |
| `cx login` | Save another account without changing the active account. |
| `cx login --device-auth` | Sign in with a device code. |
| `cx add` | Save the current Codex account. |
| `cx user@example.com` | Activate a saved account. |

Close Codex before switching. Then run:

```sh
cx user@example.com
codex
```

You can also run `uv run cx.py` with the same arguments.
At zero percent, `cx` shows the reset date in the host time zone.

Keep `config.toml` beside the script.
By default, active credentials are in `~/.codex/auth.json`.
Saved accounts are in `~/.codex/cx/accounts/`.
`CODEX_HOME` overrides the configured Codex folder.
Do not share credential files.

Set file storage in the Codex configuration:

```toml
cli_auth_credentials_store = "file"
```
