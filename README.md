# dotfiles

Personal macOS command-line configuration files.

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
