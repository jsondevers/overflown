# Setting up Vim

## Tutorial followed along from ThePrimeagen

### Files

- `init.lua` - main configuration file for Neovim

### Commands when navigating files

- `%` - create a new file
- `:Ex` - stands for "explore"

### Commands when editing files

- `:so` - source a file

```lua
vim.g.mapleader = " "
vim.keymap.set("n", "<leader>pv", vim.cmd.Ex)
```

the following will let you do a `space` + `pv` to open up the file explorer
