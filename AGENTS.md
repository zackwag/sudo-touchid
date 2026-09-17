# AGENTS.md

## Project overview

sudo-touchid is a single Bash script that enables Touch ID authentication for `sudo` on macOS Sonoma+, by managing `/etc/pam.d/sudo_local` (which persists across macOS updates). Distributed via Homebrew.

## Setup

No dependencies. Just `chmod +x sudo-touchid` if running from a clone.

## Build / Run

No build step — it's a plain Bash script.

```bash
sudo ./sudo-touchid               # enable Touch ID for sudo
sudo ./sudo-touchid --disable     # disable
sudo ./sudo-touchid --status      # check current state
sudo ./sudo-touchid --with-reattach   # also add pam_reattach.so for tmux/screen
```

## Test

No automated test suite exists — this script edits system PAM configuration, which isn't practical to unit test in CI. Verify changes manually on macOS via `--status` after enabling/disabling.

## Repository structure

- `sudo-touchid` — the entire tool (single Bash script)
- `.github/workflows/update-homebrew.yml` — on release, auto-updates the formula in the `homebrew-tap` repo with the new version and sha256

## Commit and PR conventions

- Commit messages and PR titles must follow [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `test:`, `ci:`, `build:`, `perf:`, `style:`, `revert:`), optionally with a scope, e.g. `fix(api): handle null response`.
- This repo squash-merges pull requests only; the PR title becomes the final commit message on `main`.
- A "Conventional Commits" CI check enforces this on both PR titles and direct-push commit messages.
- Branch protection on `main`: no force-pushes, no branch deletion, required status checks must pass.
