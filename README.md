# dotfiles

Personal macOS configuration files.

## Managed files

- `.config/starship.toml`: Starship prompt configuration with Conda, user,
  hostname, full path, Git branch, and Git status.

The active Starship configuration is linked from:

```text
~/.config/starship.toml -> ~/dev/dotfiles/.config/starship.toml
```

## Dependencies

```zsh
brew install starship
brew install --cask font-caskaydia-mono-nerd-font
```

Zsh initializes Starship with the following line in `~/.zshrc`:

```zsh
eval "$(starship init zsh)"
```

## Clash Verge Rev theme

`.config/clash-verge/theme.yaml` contains the saved Nord color settings and
system-following theme mode, extracted from Clash Verge Rev 2.5.4. Custom CSS
injection is currently empty, so there is no separate CSS file to maintain.

Clash Verge reads these fields from
`~/Library/Application Support/io.github.clash-verge-rev.clash-verge-rev/verge.yaml`.
The repository file is a theme source/backup, not an automatically loaded file.
Do not symlink it over the full application configuration.

To apply changes or restore on another Mac:

1. Fully quit Clash Verge Rev so it cannot overwrite the configuration.
2. Back up the local `verge.yaml` outside this repository.
3. Replace only the top-level `theme_mode` and `theme_setting` entries with those
   in `.config/clash-verge/theme.yaml`, preserving all other entries.
4. Start Clash Verge Rev and check the appearance.

After adjusting the theme in the app, copy these two entries back to the repository
file. Keep subscriptions, proxy settings, logs, and other runtime data out of Git.
