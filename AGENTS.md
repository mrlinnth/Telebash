# Repository Guidelines

## Project Structure & Module Organization
This repository is intentionally small:
- `telebash` is the main Bash entrypoint and contains all runtime logic.
- `README.md` documents setup and usage.
- `LICENSE` contains the project license.

User-specific configuration is expected in `~/.config/telebash/`, including:
- `telebash_token.txt` for the Telegram bot token
- `favorites.txt` for saved chat IDs

## Build, Test, and Development Commands
There is no build step. Use these commands during development:
- `chmod +x telebash` makes the script executable after checkout.
- `./telebash --help` prints the CLI usage and is the quickest smoke test.
- `./telebash --update` checks Telegram API access and token loading.
- `shellcheck telebash` is the preferred static check when available.

## Coding Style & Naming Conventions
Follow the existing Bash style in `telebash`:
- Use Bash syntax, not plain POSIX sh.
- Keep function names lowercase with camel-free words, for example `sendMessage` or `checkEnv`.
- Use uppercase names for constants and environment-derived variables, such as `TG_TOKEN_FILE`.
- Quote variable expansions unless word splitting is intentional.
- Keep shell output and option flags aligned with the current CLI style, such as `-t|--text`.

## Testing Guidelines
There is no automated test suite in the repository. Validate changes by:
- Running `shellcheck telebash` for syntax and quoting issues.
- Exercising the affected command path locally, for example `./telebash --help` or `./telebash --favorites`.
- Verifying token and favorites handling against files in `~/.config/telebash/`.

## Commit & Pull Request Guidelines
Git history uses short, imperative subjects such as `Update README.md` and `Send to the favorites chat by default`.
- Keep commits focused on one logical change.
- Use a concise subject that describes the user-visible effect.
- In pull requests, summarize what changed, how it was verified, and any Telegram-side setup required.
- Include sample terminal output when the change affects CLI behavior.

## Security & Configuration Tips
Do not commit Telegram tokens or personal chat IDs. Treat `~/.config/telebash/telebash_token.txt` and `favorites.txt` as local-only secrets.
