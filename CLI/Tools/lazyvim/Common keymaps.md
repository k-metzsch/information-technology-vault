
## Window Navigation & Management

| Action                  | Keymap                | Notes                                |
|-------------------------|-----------------------|--------------------------------------|
| Move focus              | `<C-h>`, `<C-j>`, `<C-k>`, `<C-l>` | Move to left/down/up/right window    |
| Split window vertically | `<leader>wv`          | (from LazyVim: Window > Vertical)    |
| Split window horizontally| `<leader>wh`         | (Window > Horizontal)                |
| Close window            | `<leader>wc`          | (Window > Close)                     |
| Maximize window         | `<leader>wx`          | (Window > Maximize/Equalize)         |
| Rotate windows          | `<leader>wr`          | (Window > Rotate)                    |
| Move window             | `<leader>wH`, `<leader>wJ`, `<leader>wK`, `<leader>wL` | Move window left/down/up/right       |

---

## Buffer Navigation & Management

| Action             | Keymap                | Notes                    |
|--------------------|-----------------------|--------------------------|
| Next buffer        | `<Tab>`               |                          |
| Previous buffer    | `<S-Tab>`             | Shift+Tab                |
| Close buffer       | `<leader>bd`          | Delete buffer            |
| Close all but this | `<leader>bD`          | Delete other buffers     |
| List buffers       | `<leader>bb`          | Telescope buffer list    |
| Pick buffer        | `<leader>bp`          | Pick buffer (bufferline) |

---

## Tab Management

| Action                | Keymap            |
|-----------------------|-------------------|
| Next tab              | `gt`              |
| Previous tab          | `gT`              |
| New tab               | `<leader>tn`      |
| Close tab             | `<leader>tc`      |

---

## Cursor Movement

| Action                | Keymap            | Notes                        |
|-----------------------|-------------------|------------------------------|
| Move to start of line | `0`               |                              |
| Move to end of line   | `$`               |                              |
| Jump by word          | `w`, `e`, `b`     |                              |
| Move up/down 10 lines | `10j`, `10k`      | Or `gj`/`gk` for wrapped     |
| Jump to top/bottom    | `gg`, `G`         | Top/bottom of buffer         |
| Jump to matching      | `%`               | Matching bracket/parenthesis |
| Jump to next/prev change | `g;`, `g,`     | Next/prev change             |

---

## Editing & Selection

| Action                    | Keymap                | Notes                          |
|---------------------------|-----------------------|--------------------------------|
| Select all                | `ggVG`                | Visual select whole file       |
| Edit all occurences       | `<C-n>` (with [vim-abolish](https://github.com/tpope/vim-abolish) or [vim-visual-multi](https://github.com/mg979/vim-visual-multi)) | Multi-cursor                  |
| Edit word under cursor    | `*` (search), then `cgn` | Change next match             |
| Select word under cursor  | `viw`                 | Visual inner word              |
| Select line               | `V`                   | Visual line                    |
| Select block (column)     | `<C-v>`               | Visual block mode              |
| Indent selection          | `>` / `<`             | After visual selection         |
| Edit selected             | `c`, `d`, `y`, etc.   | Visual mode edit/cut/yank      |
| Duplicate line            | `<leader>y` (LazyVim) | Custom LazyVim mapping         |
| Comment selection         | `gc` (with [Comment.nvim](https://github.com/numToStr/Comment.nvim)) | Toggle comment                |
| Format selection          | `=` (normal)          | Format code                    |

---

## Multi-cursor & Search-based Editing

If you have [vim-visual-multi](https://github.com/mg979/vim-visual-multi) or [nvim-cursorword](https://github.com/itchyny/vim-cursorword):

| Action               | Keymap                | Notes                       |
|----------------------|-----------------------|-----------------------------|
| Add cursor to word   | `<C-n>`               | Next occurrence             |
| Select all matches   | `\\A` (vim-visual-multi)| Select all occurrences      |
| Edit all matches     | Type as usual         | Edits all cursors           |
| Skip match           | `<C-x>`               | Skip current occurrence     |
| Remove cursor        | `q` (in visual-multi) | Remove current cursor       |

---

## File Navigation & Search

| Action                  | Keymap                  | Notes                           |
|-------------------------|-------------------------|---------------------------------|
| Find file               | `<leader>ff`            | Telescope find files            |
| Live grep               | `<leader>fg`            | Telescope live grep             |
| Go to file in buffer    | `<leader>fb`            | Telescope buffers               |
| Recent files            | `<leader>fr`            | Telescope recent files          |
| Go to definition        | `gd`                    | LSP go to definition            |
| Go to references        | `gr`                    | LSP references                  |
| Rename symbol           | `<leader>rn`            | LSP rename                      |
| Code actions            | `<leader>ca`            | LSP code actions                |

---

## Diagnostics & Quickfix

| Action                  | Keymap                  | Notes                           |
|-------------------------|-------------------------|---------------------------------|
| Show diagnostics        | `<leader>cd`            | Show diagnostics                |
| Next diagnostic         | `[d`                    | Previous: `]d`                  |
| Open quickfix           | `:copen`                | Open quickfix window            |
| Next quickfix item      | `:cnext`                | Previous: `:cprev`              |

---

## Terminal & Command Mode

| Action                  | Keymap                  | Notes                           |
|-------------------------|-------------------------|---------------------------------|
| Open terminal           | `<leader>ft`            | Open floating terminal          |
| Toggle terminal         | `<leader>tt`            | Toggle terminal (LazyVim)       |
| Normal mode in terminal | `<C-\><C-n>`            | Escape to normal mode           |

---

## Miscellaneous

| Action                  | Keymap                  | Notes                           |
|-------------------------|-------------------------|---------------------------------|
| Save file               | `<C-s>`                 | Save in insert/normal mode      |
| Quit                    | `<leader>qq`            | Quit Neovim                     |
| Reload config           | `<leader>r`             | Reload Neovim config            |
| Toggle file explorer    | `<leader>fe`            | Toggle Neo-tree                 |
