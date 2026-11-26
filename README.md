# dotfiles

Personal configuration files for macOS and Linux. Set up each app's files on
the machines where you use it.

## Managed files

- `.config/starship.toml`: Starship prompt configuration with Conda, user,
  hostname, full path, Git branch, and Git status.

The active Starship configuration is linked from:

```text
~/.config/starship.toml -> ~/dev/dotfiles/.config/starship.toml
```

## Starship setup on macOS

```zsh
brew install starship
brew install --cask font-caskaydia-mono-nerd-font
```

Zsh initializes Starship with the following line in `~/.zshrc`:

```zsh
eval "$(starship init zsh)"
```

## Ghostty appearance on macOS and Linux

`.config/ghostty/config.ghostty` sets the terminal theme, font size, and window
padding. Skip this setup on machines without Ghostty.

If you are starting with no Ghostty config under `${XDG_CONFIG_HOME:-$HOME/.config}`,
run this from the repository root to link the shared settings:

```sh
ghostty_config_dir="${XDG_CONFIG_HOME:-$HOME/.config}/ghostty"
mkdir -p "$ghostty_config_dir"
ln -s "$PWD/.config/ghostty/config.ghostty" "$ghostty_config_dir/config.ghostty"
```

If you already have an XDG Ghostty config, you can add a `config-file` entry
pointing to the absolute path of the shared file. Ghostty reads the included
file after the containing file.

On macOS, `.config/ghostty/macos.ghostty` selects CaskaydiaMono Nerd Font Mono
and integrates the tab bar into the title bar. After installing the font from
the Homebrew command above, add this line to
`~/Library/Application Support/com.mitchellh.ghostty/config.ghostty`, replacing
`/path/to/dotfiles` with the absolute path to your checkout.

```text
config-file = /path/to/dotfiles/.config/ghostty/macos.ghostty
```

On Linux, Ghostty uses its default font with the shared config. If you have
CaskaydiaMono installed there too, you can set `font-family` in your local
Ghostty config.

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
