## e.g

```lua
local map = vim.keymap.set

-- Select all
map("n", "<leader>a", "ggVG", { desc = "Select entire buffer" })

-- Quick save
map("n", "<leader>w", "<cmd>w<cr>", { desc = "Write buffer" })

-- Toggle relative number
map("n", "<leader>un", function()
  vim.opt.relativenumber = not vim.opt.relativenumber:get()
end, { desc = "Toggle relative number" })

-- Replace word under cursor (prompts)
map("n", "<leader>rw", ":%s/\\<<C-r><C-w>\\>//g<Left><Left>", { desc = "Substitute word under cursor" })
```
