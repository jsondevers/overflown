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

### horizontal moving

- `_` - move to the first character of the line
- `$` - move to the end of the line
- `d$` - delete from cursor to end of line
- `f + <character>` - find the next occurrence of the character
- `F + <character>` - find the previous occurrence of the character
- `t + <character>` - find the next occurrence of the character, but move one character before it
- `T + <character>` - find the previous occurrence of the character, but move one character after it
- `;` - repeat command in forward direction
- `,` - repeat command in backward direction
- `I` - insert at the beginning of the line
- `A` - append at the end of the line
- `o` - open a new line below the current line
- `O` - open a new line above the current line

A window contains a buffer and a buffer contains a representation of a file in memory.

### vertical moving

- `H` - move to the top of the window
- `M` - move to the middle of the window
- `L` - move to the bottom of the window
- `gg` - move to the top of the file
- `G` - move to the bottom of the file
- `{` - move by paragraph up
- `}` - move by paragraph down
- `w` - move by word forward
- `b` - move by word backward
- `e` - move to the end of the word
- `Ctrl + d` - move down half a page
- `Ctrl + u` - move up half a page
- `100` - move to line 100
- `*` - move to the next occurrence of the word under the cursor
- `#` - move to the previous occurrence of the word under the cursor
- `N` - repeat the last search in the opposite direction
- `n` - repeat the last search in the same direction
