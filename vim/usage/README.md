# [`Text Editors`](https://missing.csail.mit.edu/2020/editors/)

## `Vim`

- many things support a vim emulation mode (browser, shell, and more)
- modal editor (multiple operating modes)
- using the mouse is annoying

## `normal mode`

- entered via the `<esc>`
- most of time spent in vim
- used for making navigation

## `insert mode`

- entered via the `i` key
- put into a buffer
- used for edits

## `replace mode`

- entered through `R` key
- overwrite text

## `visual mode`

- entered through `V` key
- select text
- line (entered via `Shift-V`)
- block (entered via `Ctrl-V`)

## `command line mode`

- entered via the `:` key

## some programmers rebind keys

- some programmers rebind the normal key entering key, `<esc>`, because it's annoying to reach with the pink, they bind it to the caps lock instead `<CAPS LOCK>`

## notation

1. bare keys are represented as just the key, for example, `i`
2. key bindings: `^V` is the same as `Ctrl-V` or `<C-V>`

## basics

### starting vim

```bash
vim
```

- that's it
- (configure vim to make it pretty)

### command line for vim

- enter command line mode via `:` from `normal mode`
- `ctrl-c` doesn't quit
- `:q` will quit the program (q for quit)
- `:w` will save the program (w for write)
- `:wq` save and quit
- `:e <name of file>` open file for editing
- `:ls` show current open buffers
- `:help :w` will show help for the `:w` command
- `:help w` will show help for the `w` command

### multiple open files

- vim has open buffers that maintain a set of files
- can have number of tabs and tabs can have windows
- there isn't a 1:1 for tabs and windows
- this allows us to see the changes we're making in the same file
- when you `:q` out, it will only close the tab that we were using at the top
- `:qa` will quit all

### `normal mode` benefits

- Vims normal mode (interface) is a programming language
- talk and use Vim as if you're programming

### Buffers, tabs, and windows

- Vim maintains a set of open files, called “buffers”
- A Vim session has a number of tabs, each of which has a number of windows (split panes)
- Each window shows a single buffer
- Unlike other programs you are familiar with, like web browsers, there is not a 1-to-1 correspondence between buffers and windows; windows are merely views
- A given buffer may be open in multiple windows, even within the same tab
- This can be quite handy, for example, to view two different parts of a file at the same time

### `the key keys` (in normal mode)

#### `movement`

- using the `hjkl` keys (not the arrow keys)
- `j` moves down
- `k` moves up
- `h` moves left
- `l` moves right

#### `words`

- `w` will move forward by 1 word (w for word)
- `b` will move backward by 1 word (b for backward)
- `e` will move to end of the word (e for end of word)

#### `lines`

- `0` moves to the start of a line
- `$` moves to the end of a line
- `^` moves to first non-empty character on a line

#### `screen`

- `L` move to lowest point on screen (l for lowest)
- `M` move to middle point on screen (m for middle)
- `H` move to highest point on screen (h for highest)

#### `scroll`

- `<ctrl-u>` scroll up
- `<ctrl-d>` scroll down

#### `file`

- `<g-g>` start of fil
- `<G>` end of file

#### `line numbers`

- `:{number}<CR>`
- `{number}G (line {number})`

#### `find`

- `f <key>` will `find first` a certain character, `fc` will find the first c
- `F <key>` will `find before` a certain character
- `t <key>`
- `T <key>`
- after finding keys, use `,` and `;` for toggling matches

#### `search`

- `/<regex>`, `n` and `N` for navigating matches

#### `editing commands`

- `o` (add below), switches to insert mode and creates a newline below
- `O` (add above), switches to insert mode and creates a newline above
- `d + <movement key>` delete a word in a direction
- `u` is undo, note: undo will undo all the changes you've made, so if you went in `insert mode` and you made a bunch of changes, then went to normal mode and clicked `u`, it would undo everything you just did
- `ctrl+r` is redo
- let's say we were in the middle of a word and our cursor was at located at activ`i`ties, how would we delete to the end of this word? you would do `d + e` and this would result in activ
- `c + <movement key>` is change command, it's similar to delete `d` but it switches to `insert mode` so that you can edit and insert
- `d + d` will delete the line
- `c + c` will delete line and switch to insert mode
- `x` will delete the character the cursor is one
- `r + <character>` will replace that character with a character argument
- `y + <movement key>` to copy
- `y + y` is copy line
- `y + w` is copy word
- `p` to paste
- `~` will change the case of what you have selected
- `<count> + <movement key>` will move count spaces in `movement spaces` direction
- `.` will repeat the last edit made and paste it

#### `multiple windows`

- `:sp` and `:vsp` to split windows
- can have multiple split views on the same buffer

#### `visual mode editing`

- enter via `v` from normal mode
- using the commands above, we can select parts of text in this mode and select block of texts
- once selecting the text, you can do a bunch of useful things, for example, copying a block, so after selecting hitting `y` and it will put you back in normal mode and you can somewhere else and click `p`
- `visual line mode` can be entered via `V`
- `visual block mode` can be entered via `ctrl + v`
- can mix so many things together like `3 e` to select 3 words
- `7 + d + w` will delete 7 words, really neat

#### `modifiers`

- `c2w` will change two words, so it'll delete two words and switch you to `insert mode`

example

```bash
[shown](link name)
```

- in the example above if we did `ci[` this would `change inside bracket` and get rid of the 'shown' inside the square brackets
- if your cursor is on a different type of grouping things either `() or []`, you can use `%` to switch back and forth between the opening and closing
- something like `d + a + (` will delete everything inside the parentheses including the actual parentheses so in the example above, the `(link name)` will be deleted
- `vim golf` for fun ways to try vim

#### advanced vim

- `:s` substitute.

#### example: `%s/foo/bar/g`

- replace foo with bar globally in file

#### example: `%s/\[.*\](\(.*\))/\1/g`

- replace named Markdown links with plain URLs
