# gitsigns.nvim
Git signs written in pure lua.

WIP

#### Features:

- Signs for added, removed, and changed lines
- Asynchronous using [luv](https://github.com/luvit/luv/blob/master/docs.md)
- Navigation between diff blocks (hunks)
- Stage partial diffs
- Customisable (signs, highlights, mappings, etc)
- Status bar integration

## Requirements
Neovim nightly

## Installation

[packer.nvim](https://github.com/wbthomason/packer.nvim):
```lua
use 'nvim-lua/plenary.nvim'
use 'lewis6991/gitsigns.nvim'
```

[vim-plug](https://github.com/junegunn/vim-plug):
```vim
Plug 'nvim-lua/plenary.nvim'
Plug 'lewis6991/gitsigns.nvim'
```

## Usage

For basic setup with all batteries included:
```lua
require('gitsigns').setup()
```

Configuration can be passed to the setup function. Here is an example with all the default settings:
```lua
require('gitsigns').setup {
  signs = {
    add          = {hl = 'GitSignsAdd'   , text = '│'},
    change       = {hl = 'GitSignsChange', text = '│'},
    delete       = {hl = 'GitSignsDelete', text = '_'},
    topdelete    = {hl = 'GitSignsDelete', text = '_'},
    changedelete = {hl = 'GitSignsChange', text = '~'},
  },
  keymaps = {
    [']c']         = '<cmd>lua require("gitsigns").next_hunk()<CR>',
    ['[c']         = '<cmd>lua require("gitsigns").prev_hunk()<CR>',
    ['<leader>hs'] = '<cmd>lua require("gitsigns").stage_hunk()<CR>',
    ['<leader>gh'] = '<cmd>lua require("gitsigns").get_hunk()<CR>'
  },
  watch_index = {
    enabled = true,
    interval = 1000
  }
}
```

For information on configuring neovim via lua please see [nvim-lua-guide](https://github.com/nanotee/nvim-lua-guide).

## Status Line
WIP