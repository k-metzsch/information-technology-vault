---
title: Nice-to-Know
tags:
  - neovim
  - lazyvim
  - keymaps
  - productivity
created: 2025-08-17
---

## Legend
- `<leader>` = `Space`
- `<localleader>` = `\` (backslash)
- `<C-?>` = Control
- `<A-?>` = Alt/Meta
- `[…]` = Optional / context
- NORMAL mode unless stated otherwise

---

## 1. Edit All Occurrences / Multi-Occurrence Editing

While LazyVim does not ship a traditional multi‑cursor plugin by default, you can efficiently edit repeated text:

Core / Built-in patterns:
- `*` : Search word under cursor forward (highlights all).  
  Then use `n`/`N` to jump.
- `#` : Search word under cursor backward.
- `gn` : Select next search match for editing (visual selection). Combine with `c`:
  - Workflow: Put cursor on target word → `*` → `cgn` to change first match → type replacement → `.` to repeat change for next match; continue pressing `.` to advance/replace subsequent matches.
- `:%s/<C-r><C-w>/<replacement>/g` : Substitute all occurrences of word under cursor in file.
- Add confirmation: `:%s/<C-r><C-w>/<replacement>/gc`
- Restrict to visual selection:
  - Visually select area → `:s/pattern/replacement/g`
- Change next match only once without search prompt:
  - Use `cgn` repeatedly (as above).

Block (column) edits:
- `<C-v>` (VISUAL BLOCK) → move to span lines → `I` (insert before) or `A` (append after) → type text → `<Esc>` (applies to all selected lines).

Surround edits (mini.surround):
- `ysiw"` : Add `"` surround to inner word.
- `cs"'` : Change surrounding `"` to `'`.
- `ds"` : Delete surrounding `"`.

Comment toggling (mini.comment):
- `gc` + motion (e.g. `gcc` for current line, `gc}` until paragraph end).

---

## 2. Select All

Neovim standard (works in LazyVim):
- `ggVG` : Select entire buffer (linewise).
- `ggvG$` : Select entire buffer precisely to last character.
- `:%y` : Yank whole buffer.
- `:%d` : Delete all (be careful).
- `:%s/foo/bar/g` : Replace in entire file.

Optional custom mapping suggestion (not default):
```lua
-- in lua/config/keymaps.lua
vim.keymap.set("n", "<leader>a", "ggVG", { desc = "Select entire buffer" })
```

---

## 3. Navigate Between Windows (Splits) & Manage Layout

Move focus (LazyVim maps the directional keys):
- `<C-h>` `<C-j>` `<C-k>` `<C-l>` : Move to left / down / up / right split.

Split creation (leader window group):
- `<leader>w-` : Horizontal split (below).
- `<leader>w|` : Vertical split (right).
- `<leader>wd` : Close current window.
- `<leader>wo` or `<C-w>o` : Keep only current window.
- `<leader>wm` : Toggle maximize (uses mini.misc / plugin support if present).

Resize (commonly configured defaults):
- `<A-Left>` / `<A-Right>` : Resize vertical size (shrink/grow).
- `<A-Up>` / `<A-Down>` : Resize horizontal size.
(If these don’t work in your terminal, check terminal key transmission or adjust in `keymaps.lua`.)

Cycle windows:
- `<leader>ww` : Cycle through windows (if mapped; fallback: `<C-w>w` built-in).

Quick window commands (built-in):
- `<C-w>q` : Quit window.
- `<C-w>=` : Equalize sizes.
- `<C-w>H/J/K/L` : Move current window to edge (rearrange).

---

## 4. Navigate Buffers & Tabs

Buffers (LazyVim defaults):
- `<S-l>` : Next buffer.
- `<S-h>` : Previous buffer.
- `<leader>bd` : Delete (close) current buffer.
- `<leader>bD` : Delete all buffers but current (aka wipe others).
- `<leader>bb` : Pick buffer (buffer switcher via telescope/picker).
- `<leader>bp` : Pin/unpin buffer (if buffer pin plugin active).
- `<leader>bo` : Close all unpinned buffers.

Tabs (if you use them):
- `:tabnew` / `:tabclose` standard.
- `<leader><tab>n` : New tab (commonly mapped).
- `<leader><tab>l` : Next tab.
- `<leader><tab>h` : Previous tab.
- `<leader><tab>d` : Close current tab.

---

## 5. File / Project Navigation (Telescope & Explorer)

Telescope (core LazyVim):
- `<leader>ff` : Find files.
- `<leader>fg` : Live grep.
- `<leader>fb` : Buffers list.
- `<leader>fh` : Help tags.
- `<leader>fs` : Search current word (grep).
- `<leader>fr` : Recent files.

File tree (Neo-tree default binding):
- `<leader>e` or `<leader>fe` : Toggle file explorer.
Inside Neo-tree:
- `l` / `h` : Expand / collapse.
- `<Space>` or `a` : (depending) stage git item or add file.
- `s` : Open in split.
- `v` : Vertical split.
- `t` : New tab.

---

## 6. Scrolling & View Adjustments

Standard:
- `<C-d>` : Scroll half-page down (centers near bottom).
- `<C-u>` : Scroll half-page up.
- `<C-f>` : Full page down.
- `<C-b>` : Full page up.
- `<C-e>` : Scroll viewport down one line (cursor stays).
- `<C-y>` : Scroll viewport up one line.
- `zz` : Center cursor line.
- `zt` : Cursor line to top.
- `zb` : Cursor line to bottom.
- `z.` : Center and redraw with cursor at middle (respect folds).
- `H/M/L` : Move cursor to top/middle/bottom of screen.

Preview / folds:
- `zr` : Open (reduce folding) one level.
- `zR` : Open all folds.
- `zm` : Fold more.
- `zM` : Close all folds.
- `za` : Toggle fold under cursor.
- `zi` : Toggle folding on/off.

---

## 7. Motion / Jump Enhancements

Flash (included by LazyVim):
- `s` : Trigger flash jump (two-character pattern jump).
- `S` : Treesitter-based search.
- `r` (operator-pending) : Remote flash (apply operator to remote text).
- `R` : Treesitter nodes.
- `c` (while in Flash mode) : Jump & enter change.

Core quick movements:
- `w`, `b`, `e`, `ge` : Word motions.
- `f{char}` / `t{char}` : Find / till char on line.
- `;` / `,` : Repeat forward / backward last `f/t/F/T`.
- `%` : Match pair (brackets, etc.).
- `[` `]` : Various textobject / diagnostic motions (see diagnostics below).

---

## 8. LSP Essentials (When a Language Server Is Attached)

- `K` : Hover documentation.
- `gd` : Go to definition.
- `gD` : Go to declaration.
- `gr` : References (Telescope).
- `gi` : Implementations.
- `gt` : Type definition.
- `<leader>ca` : Code action.
- `<leader>cr` or `grn` (depending) : Rename symbol.
- `<leader>cf` : Format (async).
- `<leader>cl` : LSP info/log.
- Diagnostics:
  - `[d` / `]d` : Prev / next diagnostic.
  - `<leader>cd` : Line diagnostics (float).
  - `<leader>cq` : Populate quickfix with diagnostics.

---

## 9. Git (LazyVim Defaults with gitsigns & Integration)

- `<leader>gg` : Open LazyGit (if installed).
- `<leader>gb` : Git blame line (virtual text toggle).
- `<leader>gB` : Full file blame.
- `<leader>gs` : Stage hunk.
- `<leader>gS` : Stage buffer.
- `<leader>gr` : Reset hunk.
- `<leader>gR` : Reset buffer.
- `<leader>gp` : Preview hunk.
- `<leader>gd` : Diff (current vs index).
- `<leader>gD` : Diff (current vs last commit).
- `]c` / `[c` : Next / previous hunk.

---

## 10. Quick Editing Helpers

Comments:
- `gcc` : Toggle comment on line.
- `gc{motion}` : Toggle comment over motion.
- `gb{motion}` : Block comment (if supported).

Surround (mini.surround):
- `ys{motion}{char}` : Add surround.
- `ds{char}` : Delete surround.
- `cs{old}{new}` : Change surround.

Text Objects (Treesitter):
- `vai` / `vi(` / `va{` etc.: Select around/inside functions, classes depending on parser, typically:
  - `af` / `if` : a function / inner function
  - `ac` / `ic` : a class / inner class

Indent & shifting:
- `>>` / `<<` : Indent / unindent line or selection.
- `=` + motion : Reindent region.
- `==` : Reindent line.

Repeat & dot tricks:
- `.` : Repeat last change.
- `g;` / `g,` : Jump to previous / next change location.

Registers & clipboard:
- `"*y` or `"+y` : Yank to system clipboard (if compiled with clipboard).
- `<leader>y` : Often mapped to yank to system clipboard (check config).
- `<leader>p` : Paste from clipboard (if mapped).

---

## 11. Command & Search Mode Enhancements

- `/` : Forward search.
- `?` : Backward search.
- `n` / `N` : Repeat search forward / backward.
- `q:` : Command-line window history.
- `q/` : Search history.
- `<C-r><C-w>` (in command-line) : Insert word under cursor.
- `:noh` or `<leader>sn` : Clear search highlight (LazyVim often maps).
- `/\V` : Very nomagic literal search start.

---

## 12. Diagnostics & Trouble (if trouble.nvim enabled)

- `<leader>xx` : Toggle Trouble (general list).
- `<leader>xw` : Workspace diagnostics.
- `<leader>xd` : Document diagnostics.
- `<leader>xq` : Quickfix list.
- `<leader>xl` : Location list.
- `<leader>xr` : LSP references.

---

## 13. Terminal / Toggle Tools

- `<leader>ft` : Toggle terminal (floating).
- `<leader>fT` : New terminal instance.
Inside terminal:
- `<Esc>` or `<C-\><C-n>` : Return to NORMAL mode.

---

## 14. Sessions / Persistence (if persistence plugin active)

- `<leader>qs` : Restore last session.
- `<leader>ql` : Restore last session for current dir.
- `<leader>qd` : Stop saving session.

---

## 15. Snippets & Completion

Completion (nvim-cmp):
- `<C-Space>` : Trigger completion menu.
- `<CR>` : Confirm selection.
- `<Tab>` / `<S-Tab>` : Next / previous item or jump in snippet.
Snippets (LuaSnip):
- `<Tab>` : Jump to next snippet placeholder (in snippet context).
- `<S-Tab>` : Jump backward.

---

## 16. Useful “Glue” Sequences for Productivity

- Search & replace word under cursor globally with confirmation:
  - `:%s/\<<C-r><C-w>\>/<replacement>/gc`
- Rename symbol with LSP (after rename, run substitution fallback if symbol isn’t LSP-managed):
  - `<leader>cr` then check references with `gr`.
- Change all matches incrementally:
  - `*` → `cgn` (type) → `<Esc>` → `.` → `.` … repeat.
- Convert selected lines to sorted unique:
  - VISUAL select → `:sort u`
- Format & organize imports (if server supports):
  - `<leader>cf`

---

## 18. Troubleshooting Missing Keymaps

If a suggested keymap doesn’t work:
1. Run `:Telescope keymaps` to inspect active maps.
2. Confirm plugin is loaded (LazyVim lazy-loads): open a relevant file type.
3. Check `lua/config/keymaps.lua`.
4. Remove conflicting user map with `vim.keymap.del(mode, lhs)`.
5. Use `:verbose map <lhs>` to see origin.

---

## 19. Minimal Mental Model

Category → Anchor Key:
- Buffers → Shift-h/Shift-l
- Files & Project → `<leader>f…`
- Git → `<leader>g…`
- LSP → `<leader>c…` (code) + `g{letter}` (goto)
- Windows → `<leader>w…` + `<C-h/j/k/l>`
- Search → `/`, `*`, `gc` (comment), `s` (Flash)
- Diagnostics → `<leader>x…` or `[d` `]d`

Memorize the prefixes; let which-key fill in the rest.

---

## 20. Practice Path (Daily Drill)

1. Open repo → `<leader>ff` find file.
2. Navigate splits → `<C-h/j/k/l>`.
3. Search symbol → `*` then multi-edit with `cgn` + `.`.
4. Jump quickly inside file → `s` (Flash).
5. Rename symbol → `<leader>cr`.
6. Stage hunk & preview → `<leader>gp` / `<leader>gs`.
7. Commit externally (if using LazyGit) → `<leader>gg`.
8. Format & diagnostics before save → `<leader>cf`, `[d` check.

---

## 21. Quick Reference Tables (Compact)

Scrolling:
- Half: `<C-d>` / `<C-u>`
- Full: `<C-f>` / `<C-b>`
- Line: `<C-e>` / `<C-y>`
- Center: `zz`

Window focus:
- `<C-h/j/k/l>`

Buffer cycle:
- `<S-h>` / `<S-l>`

Search occurrences:
- `*`, `#`, `cgn`, `gn`

LSP core:
- `gd`, `gr`, `gi`, `K`, `<leader>ca`, `<leader>cr`, `[d`, `]d`

Git (gitsigns):
- `<leader>gs`, `<leader>gr`, `<leader>gp`, `]c`, `[c`, `<leader>gg` (LazyGit)

---