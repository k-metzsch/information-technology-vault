
Source: keymap-default.toml from the Yazi project.

Each table lists the default key bindings (contexts):
- mgr (file manager main view)
- tasks (task manager)
- spot (spot/info view)
- pick (picker dialogs)
- input (line editor)
- confirm (confirmation dialogs)
- cmp (completion popup)
- help (help overlay)

---

## mgr (File List)

| Keys | Run | Description |
|------|-----|-------------|
| Esc | escape | Exit visual mode, clear selection, or cancel search |
| C-[ | escape | Exit visual mode, clear selection, or cancel search |
| q | quit | Quit the process |
| Q | quit --no-cwd-file | Quit without outputting cwd-file |
| C-c | close | Close the current tab, or quit if it's last |
| C-z | suspend | Suspend the process |
| k | arrow prev | Previous file |
| j | arrow next | Next file |
| Up | arrow prev | Previous file |
| Down | arrow next | Next file |
| C-u | arrow -50% | Move cursor up half page |
| C-d | arrow 50% | Move cursor down half page |
| C-b | arrow -100% | Move cursor up one page |
| C-f | arrow 100% | Move cursor down one page |
| S-PageUp | arrow -50% | Move cursor up half page |
| S-PageDown | arrow 50% | Move cursor down half page |
| PageUp | arrow -100% | Move cursor up one page |
| PageDown | arrow 100% | Move cursor down one page |
| g g | arrow top | Go to top |
| G | arrow bot | Go to bottom |
| h | leave | Back to the parent directory |
| l | enter | Enter the child directory |
| Left | leave | Back to the parent directory |
| Right | enter | Enter the child directory |
| H | back | Back to previous directory |
| L | forward | Forward to next directory |
| Space | toggle ; arrow next | Toggle the current selection state |
| C-a | toggle_all --state=on | Select all files |
| C-r | toggle_all | Invert selection of all files |
| v | visual_mode | Enter visual mode (selection mode) |
| V | visual_mode --unset | Enter visual mode (unset mode) |
| K | seek -5 | Seek up 5 units in the preview |
| J | seek 5 | Seek down 5 units in the preview |
| Tab | spot | Spot hovered file |
| o | open | Open selected files |
| O | open --interactive | Open selected files interactively |
| Enter | open | Open selected files |
| S-Enter | open --interactive | Open selected files interactively |
| y | yank | Yank selected files (copy) |
| x | yank --cut | Yank selected files (cut) |
| p | paste | Paste yanked files |
| P | paste --force | Paste yanked files (overwrite if the destination exists) |
| - | link | Symlink the absolute path of yanked files |
| _ | link --relative | Symlink the relative path of yanked files |
| C-- | hardlink | Hardlink yanked files |
| Y | unyank | Cancel the yank status |
| X | unyank | Cancel the yank status |
| d | remove | Trash selected files |
| D | remove --permanently | Permanently delete selected files |
| a | create | Create a file (ends with / for directories) |
| r | rename --cursor=before_ext | Rename selected file(s) |
| ; | shell --interactive | Run a shell command |
| : | shell --block --interactive | Run a shell command (block until finishes) |
| . | hidden toggle | Toggle the visibility of hidden files |
| s | search --via=fd | Search files by name via fd |
| S | search --via=rg | Search files by content via ripgrep |
| C-s | escape --search | Cancel the ongoing search |
| z | plugin fzf | Jump to a file/directory via fzf |
| Z | plugin zoxide | Jump to a directory via zoxide |
| m s | linemode size | Linemode: size |
| m p | linemode permissions | Linemode: permissions |
| m b | linemode btime | Linemode: btime |
| m m | linemode mtime | Linemode: mtime |
| m o | linemode owner | Linemode: owner |
| m n | linemode none | Linemode: none |
| c c | copy path | Copy the file path |
| c d | copy dirname | Copy the directory path |
| c f | copy filename | Copy the filename |
| c n | copy name_without_ext | Copy the filename without extension |
| f | filter --smart | Filter files |
| / | find --smart | Find next file |
| ? | find --previous --smart | Find previous file |
| n | find_arrow | Next found |
| N | find_arrow --previous | Previous found |
| , m | sort mtime --reverse=no ; linemode mtime | Sort by modified time |
| , M | sort mtime --reverse ; linemode mtime | Sort by modified time (reverse) |
| , b | sort btime --reverse=no ; linemode btime | Sort by birth time |
| , B | sort btime --reverse ; linemode btime | Sort by birth time (reverse) |
| , e | sort extension --reverse=no | Sort by extension |
| , E | sort extension --reverse | Sort by extension (reverse) |
| , a | sort alphabetical --reverse=no | Sort alphabetically |
| , A | sort alphabetical --reverse | Sort alphabetically (reverse) |
| , n | sort natural --reverse=no | Sort naturally |
| , N | sort natural --reverse | Sort naturally (reverse) |
| , s | sort size --reverse=no ; linemode size | Sort by size |
| , S | sort size --reverse ; linemode size | Sort by size (reverse) |
| , r | sort random --reverse=no | Sort randomly |
| g h | cd ~ | Go home |
| g c | cd ~/.config | Go ~/.config |
| g d | cd ~/Downloads | Go ~/Downloads |
| g Space | cd --interactive | Jump interactively |
| g f | follow | Follow hovered symlink |
| t | tab_create --current | Create a new tab with CWD |
| 1 | tab_switch 0 | Switch to first tab |
| 2 | tab_switch 1 | Switch to second tab |
| 3 | tab_switch 2 | Switch to third tab |
| 4 | tab_switch 3 | Switch to fourth tab |
| 5 | tab_switch 4 | Switch to fifth tab |
| 6 | tab_switch 5 | Switch to sixth tab |
| 7 | tab_switch 6 | Switch to seventh tab |
| 8 | tab_switch 7 | Switch to eighth tab |
| 9 | tab_switch 8 | Switch to ninth tab |
| [ | tab_switch -1 --relative | Switch to previous tab |
| ] | tab_switch 1 --relative | Switch to next tab |
| { | tab_swap -1 | Swap current tab with previous tab |
| } | tab_swap 1 | Swap current tab with next tab |
| w | tasks:show | Show task manager |
| ~ | help | Open help |
| F1 | help | Open help |

---

## tasks (Task Manager)

| Keys | Run | Description |
|------|-----|-------------|
| Esc | close | Close task manager |
| C-[ | close | Close task manager |
| C-c | close | Close task manager |
| w | close | Close task manager |
| k | arrow prev | Previous task |
| j | arrow next | Next task |
| Up | arrow prev | Previous task |
| Down | arrow next | Next task |
| Enter | inspect | Inspect the task |
| x | cancel | Cancel the task |
| ~ | help | Open help |
| F1 | help | Open help |

---

## spot (Spot / Preview Info)

| Keys | Run | Description |
|------|-----|-------------|
| Esc | close | Close the spot |
| C-[ | close | Close the spot |
| C-c | close | Close the spot |
| Tab | close | Close the spot |
| k | arrow prev | Previous line |
| j | arrow next | Next line |
| h | swipe prev | Swipe to previous file |
| l | swipe next | Swipe to next file |
| Up | arrow prev | Previous line |
| Down | arrow next | Next line |
| Left | swipe prev | Swipe to previous file |
| Right | swipe next | Swipe to next file |
| c c | copy cell | Copy selected cell |
| ~ | help | Open help |
| F1 | help | Open help |

---

## pick (Pick Component)

| Keys | Run | Description |
|------|-----|-------------|
| Esc | close | Cancel pick |
| C-[ | close | Cancel pick |
| C-c | close | Cancel pick |
| Enter | close --submit | Submit the pick |
| k | arrow prev | Previous option |
| j | arrow next | Next option |
| Up | arrow prev | Previous option |
| Down | arrow next | Next option |
| ~ | help | Open help |
| F1 | help | Open help |

---

## input (Input / Line Editor)

| Keys | Run | Description |
|------|-----|-------------|
| C-c | close | Cancel input |
| Enter | close --submit | Submit input |
| Esc | escape | Back to normal mode, or cancel input |
| C-[ | escape | Back to normal mode, or cancel input |
| i | insert | Enter insert mode |
| I | move first-char ; insert | Move to the BOL, and enter insert mode |
| a | insert --append | Enter append mode |
| A | move eol ; insert --append | Move to the EOL, and enter append mode |
| v | visual | Enter visual mode |
| r | replace | Replace a single character |
| V | move bol ; visual ; move eol | Select from BOL to EOL |
| C-A | move eol ; visual ; move bol | Select from EOL to BOL |
| C-E | move bol ; visual ; move eol | Select from BOL to EOL |
| h | move -1 | Move back a character |
| l | move 1 | Move forward a character |
| Left | move -1 | Move back a character |
| Right | move 1 | Move forward a character |
| C-b | move -1 | Move back a character |
| C-f | move 1 | Move forward a character |
| b | backward | Move back to the start of the current or previous word |
| B | backward --far | Move back to the start of the current or previous WORD |
| w | forward | Move forward to the start of the next word |
| W | forward --far | Move forward to the start of the next WORD |
| e | forward --end-of-word | Move forward to the end of the current or next word |
| E | forward --far --end-of-word | Move forward to the end of the current or next WORD |
| A-b | backward | Move back to the start of the current or previous word |
| A-f | forward --end-of-word | Move forward to the end of the current or next word |
| C-Left | backward | Move back to the start of the current or previous word |
| C-Right | forward --end-of-word | Move forward to the end of the current or next word |
| 0 | move bol | Move to the BOL |
| $ | move eol | Move to the EOL |
| _ | move first-char | Move to the first non-whitespace character |
| ^ | move first-char | Move to the first non-whitespace character |
| C-a | move bol | Move to the BOL |
| C-e | move eol | Move to the EOL |
| Home | move bol | Move to the BOL |
| End | move eol | Move to the EOL |
| Backspace | backspace | Delete the character before the cursor |
| Delete | backspace --under | Delete the character under the cursor |
| C-h | backspace | Delete the character before the cursor |
| C-d | backspace --under | Delete the character under the cursor |
| C-u | kill bol | Kill backwards to the BOL |
| C-k | kill eol | Kill forwards to the EOL |
| C-w | kill backward | Kill backwards to the start of the current word |
| A-d | kill forward | Kill forwards to the end of the current word |
| C-Backspace | kill backward | Kill backwards to the start of the current word |
| C-Delete | kill forward | Kill forwards to the end of the current word |
| d | delete --cut | Cut selected characters |
| D | delete --cut ; move eol | Cut until EOL |
| c | delete --cut --insert | Cut selected characters, and enter insert mode |
| C | delete --cut --insert ; move eol | Cut until EOL, and enter insert mode |
| s | delete --cut --insert ; move 1 | Cut current character, and enter insert mode |
| S | move bol ; delete --cut --insert ; move eol | Cut from BOL until EOL, and enter insert mode |
| x | delete --cut ; move 1 --in-operating | Cut current character |
| y | yank | Copy selected characters |
| p | paste | Paste copied characters after the cursor |
| P | paste --before | Paste copied characters before the cursor |
| u | undo | Undo the last operation |
| C-r | redo | Redo the last operation |
| ~ | help | Open help |
| F1 | help | Open help |

---

## confirm (Confirmation Dialog)

| Keys | Run | Description |
|------|-----|-------------|
| Esc | close | Cancel the confirm |
| C-[ | close | Cancel the confirm |
| C-c | close | Cancel the confirm |
| Enter | close --submit | Submit the confirm |
| n | close | Cancel the confirm |
| y | close --submit | Submit the confirm |
| k | arrow prev | Previous line |
| j | arrow next | Next line |
| Up | arrow prev | Previous line |
| Down | arrow next | Next line |
| ~ | help | Open help |
| F1 | help | Open help |

---

## cmp (Completion Component)

| Keys | Run | Description |
|------|-----|-------------|
| C-c | close | Cancel completion |
| Tab | close --submit | Submit the completion |
| Enter | close --submit ; input:close --submit | Complete and submit the input |
| A-k | arrow prev | Previous item |
| A-j | arrow next | Next item |
| Up | arrow prev | Previous item |
| Down | arrow next | Next item |
| C-p | arrow prev | Previous item |
| C-n | arrow next | Next item |
| ~ | help | Open help |
| F1 | help | Open help |

---

## help (Help Overlay)

| Keys | Run | Description |
|------|-----|-------------|
| Esc | escape | Clear the filter, or hide the help |
| C-[ | escape | Clear the filter, or hide the help |
| C-c | close | Hide the help |
| k | arrow prev | Previous line |
| j | arrow next | Next line |
| Up | arrow prev | Previous line |
| Down | arrow next | Next line |
| f | filter | Filter help items |

---

## Notes

- Multi-stroke sequences (e.g. g g, c c, , m) must be typed in order.
- Some commands run multiple actions; these are separated by ; in the Run column.
- Modifier notation: C- = Ctrl, A- = Alt/Meta, S- = Shift.
- Former special-key bracket notation removed (Esc was <Esc>, etc.).

If you’d like a variant with backticks around key names (for Obsidian styling), or a compact version, just ask.