# fzy-tab

[fzy](https://github.com/jhawthorn/fzy)-powered tab completion for [Fish shell](https://fishshell.com/). Replaces the default list-based completion with an interactive fuzzy search interface.

## Requirements

- [Fish](https://fishshell.com/) 3.0+
- [fzy](https://github.com/jhawthorn/fzy)

## Installation

```fish
cp conf.d/fzy_tab_init.fish ~/.config/fish/conf.d/
cp functions/*.fish ~/.config/fish/functions/
```

Restart Fish or open a new terminal to activate.

## Usage

Press Tab to trigger completion. When multiple candidates are available, fzy opens an interactive fuzzy search.

| Command | Description |
|---------|-------------|
| `fzy_tab_disable` | Disable fzy completion, restore default |
| `fzy_tab_enable` | Re-enable fzy completion |
| `fzy_tab_toggle` | Toggle on/off |

## Configuration

Configured via Fish universal variables:

| Variable | Default | Description |
|----------|---------|-------------|
| `FZY_TAB_LINES` | `15` | Number of lines to show in fzy |
| `FZY_TAB_PROMPT` | `"> "` | fzy prompt string |
| `FZY_TAB_SHOW_SCORES` | `0` | Show match scores (`1` to enable) |

```fish
set -U FZY_TAB_LINES 10
set -U FZY_TAB_PROMPT "> "
set -U FZY_TAB_SHOW_SCORES 1
```

## Notes

- `z`, `zi`, and `zoxide` commands are skipped automatically, falling back to Fish default completion
- Single candidates are inserted directly without launching fzy
- No trailing space after directories; space is auto-inserted for non-directories

Sometimes fzy-tab keybinding will not work, you can override `fish_user_key_bindings` function:

```fish
# ~/.config/fish/functions/fish_user_key_bindings.fish
function fish_user_key_bindings
    bind \t _fzy_tab_complete
end
```
