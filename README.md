# dotfiles

cwalia's devenv dotfiles. Cloned to `~/dotfiles` and run via `./setup` during devenv instance provisioning; re-run `./setup` by hand any time, or `devenv rebuild` for a clean apply.

## What `setup` does

- Symlinks `zsh/` (zsh + antidote + powerlevel10k), `tmux/.tmux.conf`, `docker/config.json` (ECR credential helper) and `herdr/config.toml`.
- Writes a real `~/.gitconfig` that includes `git/gitconfig_template` (identity + shared settings).
- herdr: zsh completions, the herdr Claude skill, the `om1incubator/herdr-presets` plugin (`ha`, `prefix+a` picker) with presets from `herdr/agents.json`.
- Compiles `terminfo/*.terminfo` (Ghostty's `xterm-ghostty`) into `~/.terminfo` when the host can't resolve it, so Ghostty works over ssh on Ubuntu's older ncurses.
- Links `bin/sync-repos` into `~/.local/bin`. On the devenv, every new shell runs it in the background (at most every 4 h): it clones the repos in `repos.txt` into `~/code` (circus blob-less) and fast-forwards their `main`. It never resets, stashes or checks out; skipped repos show up as a one-line notice in your next shell. Run `sync-repos` to sync now.
- Best-effort installs of missing tools (uv, AWS CLI, SSM plugin, ECR helper); a no-op on a provisioned devenv.

Based on [pritam992/dotfiles](https://github.com/pritam992/dotfiles) and [jreslock/dotfiles](https://github.com/jreslock/dotfiles).
