
### Launch tmux

```sh
tmux
```

This starts a new tmux session.  
You’ll see your shell prompt inside tmux.

### Detach from Session

```
Ctrl+b then d
```

This leaves your session running in the background.

### Reattach to Session

List sessions:
```sh
tmux ls
```
Reattach:
```sh
tmux attach -t <session-name>
```

---

## Your Keybinds (from your config)

| Key Combo         | Action                      | Description                                               |
| ----------------- | -------------------------- | --------------------------------------------------------- |
| `C-a`             | Prefix (if set)            | Use instead of default `C-b` (Control+a).                 |
| `C-a` then `a`    | Last window                | Switch between alternate windows.                         |
| `C-p`             | Previous window            | Move to previous tmux window.                             |
| `C-n`             | Next window                | Move to next tmux window.                                 |
| `<prefix> <prefix>` | Send prefix to shell       | E.g., `C-a C-a` sends `C-a` to the shell.                 |
| `R`               | Reload config              | Reload your tmux config file and display a message.       |

**Note:**  
- `<prefix>` is your chosen prefix key (`C-a` if you changed it, else `C-b`).  
- If you use `C-a` as prefix, `C-a a` switches to previous window.

---

## Basic tmux Commands

| Action                      | Command/Keybind                      |
|-----------------------------|--------------------------------------|
| Split pane vertically       | `Ctrl+b %`                           |
| Split pane horizontally     | `Ctrl+b "`                           |
| Move between panes          | `Ctrl+b` then arrow key              |
| Close pane                  | `exit` or `Ctrl+d` in the pane       |
| Create new window           | `Ctrl+b c`                           |
| Switch window               | `Ctrl+b n` (next), `Ctrl+b p` (prev) |
| List windows                | `Ctrl+b w`                           |
| Rename window               | `Ctrl+b ,`                           |
| Kill window                 | `Ctrl+b &`                           |
| Kill session                | `tmux kill-session -t <name>`        |

---

## Advanced: Scripting Commands to tmux

To send keys to a process in a tmux pane:
```sh
tmux send-keys -t <session>:<window>.<pane> <key>
```

Example (send `r` for hot reload in Flutter):
```sh
tmux send-keys -t mysession:0.0 r
```

---

## Customizations from Your Config

- **Emacs key bindings**: Command prompt (`prefix + :`) uses Emacs keys.
- **Aggressive resize**: Windows resize to the active pane in non-iTerm terminals.
- **Scrollback history**: Up to 50,000 lines.
- **Status message time**: Displayed for 4 seconds.
- **Status refresh**: Every 5 seconds.

---

## Reloading Your Config

Press:
```
<Prefix> R
```
This reloads your tmux config file and shows a message.

---

## Tips

- Use `<prefix> ?` to list all key bindings.
- Use `<prefix> [` to enter copy mode (scroll up).
- You can change the prefix in your config and your guide will update accordingly.

---

## Troubleshooting

If colors look off in tmux, ensure your `.tmux.conf` includes:
```bash
set -g default-terminal "tmux-256color"
set -ga terminal-overrides ',*:Tc'
```

Restart tmux after changing `.tmux.conf`.
