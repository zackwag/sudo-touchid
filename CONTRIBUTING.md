# Contributing to sudo-touchid

Thanks for considering a contribution to sudo-touchid, a small shell tool that enables Touch ID for `sudo` on macOS Sonoma and later.

## Getting started

```bash
git clone https://github.com/zackwag/sudo-touchid.git
cd sudo-touchid
chmod +x sudo-touchid
```

## Development

This is a single Bash script (`sudo-touchid`) that edits `/etc/pam.d/sudo_local`. There is no build step and no automated test suite — changes should be tested manually on macOS by running the script and checking `sudo-touchid --status`.

```bash
sudo ./sudo-touchid --status
sudo ./sudo-touchid            # enable
sudo ./sudo-touchid --disable  # disable
```

Releases automatically update the `sudo-touchid` formula in [homebrew-tap](https://github.com/zackwag/homebrew-tap) via `.github/workflows/update-homebrew.yml`.

## Commit messages and pull requests

This repo uses [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, `chore:`, etc.). Pull requests are squash-merged, and the **PR title** becomes the commit on `main` — so PR titles must follow this format. This is enforced automatically by the "Conventional Commits" check.

Direct pushes to `main` are allowed but must also use a Conventional Commits-formatted commit message (validated by the same check).

## Opening a pull request

1. Fork the repo and create a branch off `main`.
2. Make your changes.
3. Open a pull request with a Conventional Commits-formatted title.
4. Wait for CI to pass — required checks must be green before merge.

## Reporting issues

Use [GitHub Issues](../../issues) for bugs and feature requests.
