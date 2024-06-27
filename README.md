# MacOS Tmux Bitwarden Plugin

This is a fork of [Alkindi42/tmux-bitwarden](https://github.com/Alkindi42/tmux-bitwarden), modified to work with zsh under MacOS.

## Requirements
- Bitwarden CLI
- fzf
- jq
- zsh

They can be installed using Homebrew:
```
% brew install bitwarden-cli fzf jq
```

zsh is the standard MacOS shell.

## Installation
### Tmux Plugin Manager
- Add the following to your `tmux.conf`:
  `set -g @plugin "johansaf/tmux-macos-bw"`
- Install the plugin by hitting `prefix+I`

## Configuration
### Key bindings
The default keybinding is `prefix+b`. This will open a new bottom pane with `bw` running.

This can be changed in `tmux.conf`:
```
set -g @bw-key "T"
```

### Node deprecation warning
When running the `bw` command, Node can give the following message:
```
% bw
(node:21467) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
(Use `node --trace-deprecation ...` to show where the warning was created)
```

One way of suppressing this message is to add the following to your `.zshenv` file:
```
export NODE_OPTIONS="--no-deprecation"
```

[Source](https://github.com/bitwarden/clients/issues/6689)

## Usage
- Type `prefix+b` (or whatever key you changed it to)
- Enter your master password
- Search for your password and hit `Enter` to have it typed into the active shell

The session is saved in-between executions so the master password only has to be entered once. To exit the session, quit tmux or invalidate the session by doing `bw logout`.

No passwords are copied to the clipboard.
