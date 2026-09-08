# sudo-touchid

Enable Touch ID for `sudo` on macOS Sonoma and later.

Uses `/etc/pam.d/sudo_local`, which persists across macOS updates.

## Install

```bash
brew install zackwag/tap/sudo-touchid
```

## Usage

```bash
# Enable Touch ID for sudo
sudo sudo-touchid

# Enable with tmux/screen support (requires pam-reattach)
sudo sudo-touchid --with-reattach

# Check current status
sudo-touchid --status

# Disable
sudo sudo-touchid --disable
```

### tmux/screen support

If you use tmux or screen, Touch ID won't work in those sessions without
[pam-reattach](https://github.com/fabianishere/pam_reattach):

```bash
brew install pam-reattach
sudo sudo-touchid --with-reattach
```

## Credit

Inspired by [artginzburg/sudo-touchid](https://github.com/artginzburg/sudo-touchid).

## License

MIT
