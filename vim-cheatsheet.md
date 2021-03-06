# VIM cheatsheet

A list of commands for Vim and Neovim.

#### Notation
* **N**      : Normal mode
* **I**      : Insert mode
* **V**      : Visual mode
* **Ex**     : Command-Line mode
* `C-<char>` : `Ctrl+<char>`
* `<leader>` : By default `\`


## Contents
* [Navigation](#navigation)
* [Edition](#edition)
* [Arithmetic](#arithmetic)
* [Undo and Redo](#undo-and-redo)
* [Search and Replace](#search-and-replace)
* [Registers](#registers)
* [Macros](#macros)
* [Visual Mode](#visual-mode)
* [Command-Line Mode](#command-line-mode)
* [Buffers, Tabs and Windows](#buffers-tabs-and-windows)
* [Files](#files)
* [Code compilation](#code-compilation)


## Navigation

| Command       | Mode | Description                             |
| ------------- | ---- | --------------------------------------- |
| `h/j/k/l`     | N    | Move cursor                             |
| `gk`          | N    | Up one display line                     |
| `gj`          | N    | Down one display line                   |
| `gg`          | N    | Move to start of file                   |
| `G`           | N    | Move to end  of file                    |
| `0`           | N    | Move to start of line                   |
| `^`           | N    | Move to first nonblank character        |
| `$`           | N    | Move to end of line                     |
| `w`/`W`       | N    | Forward to start of next word/WORD      |
| `b`/`B`       | N    | Backward to start of previous word/WORD |
| `e`/`E`       | N    | Forward to end of current word/WORD     |
| `ge`/`gE`     | N    | Backward to end of previous word/WORD   |
| `%`           | N    | Jump between matching keywords          |
| `<C-u>`       | N    | Up one half of the screen               |
| `<C-d>`       | N    | Down one half of the screen             |
| `<C-y>`       | N    | Up one line                             |
| `<C-e>`       | N    | Down one line                           |
| `zz`          | N    | Center the cursor                       |
| `<C-o>`       | N    | Go to previous jump location            |
| `<C-i>`       | N    | Go to next jump location                |
| `m{a-zA-Z}`   | N    | Mark current cursor location            |
| `` `{mark} `` | N    | Move to the line where a mark was set   |
| ` `` `        | N    | Move to position before last jump       |
| `marks`       | Ex   | Show list of marks                      |


## Edition

| Command | Mode | Description                          |
| ------- | ---- | ------------------------------------ |
| `i`     | N    | Insert a character before the cursor |
| `I`     | N    | Insert a character at start of line  |
| `a`     | N    | Append a character after the cursor  |
| `A`     | N    | Append a character at end of line    |
| `o`     | N    | Append a line below the cursor       |
| `O`     | N    | Append a line up the cursor          |
| `r`     | N    | Replace one character                |
| `R`     | N    | Replace mode                         |
| `x`     | N    | Delete character under the cursor    |
| `d`     | N    | Delete                               |
| `dd`    | N    | Delete a line                        |
| `D`     | N    | Delete to end of line                |
| `c`     | N    | Change                               |
| `cc`    | N    | Change the entire line               |
| `C`     | N    | Change to end of line                |
| `s`     | N    | Substitute a character               |
| `J`     | N    | Join lines                           |
| `>`     | N    | Increase indentation                 |
| `>>`    | N    | Increase line indentation            |
| `<`     | N    | Decrease indentation                 |
| `<<`    | N    | Decrease line indentation            |
| `~`     | N    | Swap case                            |
| `gU`    | N    | Make uppercase                       |
| `gu`    | N    | Make lowercase                       |
| `<C-w>` | I    | Delete back one word                 |
| `<C-u>` | I    | Delete back to start of line         |
| `<C-o>` | I    | Go to Normal mode for one command    |


## Arithmetic

| Command        | Mode | Description                              |
| -------------- | ---- | ---------------------------------------- |
| `<C-a>`        | N    | Increment                                |
| `<C-x>`        | N    | Decrement                                |
| `<C-r>={expr}` | I    | Evaluate and insert result of expression |


## Undo and Redo

| Command | Mode | Description        |
| ------- | ---- | ------------------ |
| `.`     | N    | Repeat last change |
| `u`     | N    | Undo last change   |
| `<C-r>` | N    | Redo last change   |


## Search and Replace

| Command         | Mode | Description                                                         |
| --------------- | ---- | ------------------------------------------------------------------- |
| `f{char}`       | N    | Forward to next occurrence of `{char}`                              |
| `F{char}`       | N    | Backward to previous occurrence of `{char}`                         |
| `t{char}`       | N    | Forward to the character before the next occurrence of `{char}`     |
| `T{char}`       | N    | Backward to the character after the previous occurrence of `{char}` |
| `;`             | N    | Repeat the last character-search command                            |
| `,`             | N    | Reverse the last character-search command                           |
| `/{pattern}`    | N    | Search pattern forward                                              |
| `?{pattern}`    | N    | Search pattern backward                                             |
| `n`             | N    | Jump to next search match                                           |
| `N`             | N    | Jump to previous search match                                       |
| `*`             | N    | Search for the word under the cursor                                |
| `\v`            | Ex   | Regex searches                                                      |
| `\V`            | Ex   | Literal searches                                                    |
| `%s/old/new/gc` | Ex   | Replace all occurrences (g) on all lines (%) with confirmation (c)  |


## Registers

| Command      | Mode | Description                 |
| ------------ | ---- | --------------------------- |
| `y`          | N    | Yank                        |
| `yy`         | N    | Yank the entire line        |
| `p`          | N    | Paste after the cursor      |
| `P`          | N    | Paste before the cursor     |
| `<C-r>{reg}` | I    | Paste content of a register |
| `reg`        | Ex   | Show registers content      |

| Register | Description               |
| -------- | ------------------------- |
| `""`     | Unnamed register          |
| `"{reg}` | Select register           |
| `"0`     | Yank register             |
| `"_`     | Black hole register       |
| `"+`     | System clipboard register |
| `"*`     | Selection register        |
| `"=`     | Expression register       |
| `"%`     | Filename register         |


## Macros

| Command  | Mode | Description                     |
| -------- | ---- | ------------------------------- |
| `q{a-z}` | N    | Record a macro                  |
| `q`      | N    | Stop recording macro            |
| `@{a-z}` | N    | Play a macro                    |
| `@@`     | N    | Replay most recently used macro |


## Visual Mode

| Command | Mode | Description                            |
| ------- | ---- | -------------------------------------- |
| `v`     | N    | Enable visual mode                     |
| `V`     | N    | Enable line-wise visual mode           |
| `<C-v>` | N    | Enable block-wise visual mode          |
| `gv`    | N    | Reselect last visual selection         |
| `o`     | V    | Go to the other end of higlighted text |


## Command-Line Mode

| Command      | Mode | Description                                     |
| ------------ | ---- | ----------------------------------------------- |
| `:`          | N    | Enable Command-Line mode                        |
| `@:`         | N    | Repeat last Ex command                          |
| `<C-f>`      | Ex   | Switch to the command-line window               |
| `<C-r><C-w>` | Ex   | Insert the current word into the command prompt |
| `!<cmd>`     | Ex   | Run a shell command                             |
| `shell`      | Ex   | Start an interactive shell session              |
| `terminal`   | Ex   | Create a terminal buffer                        |
| `set spell`  | Ex   | Enable spell checker                            |
| `z=`         | Ex   | Suggest corrections for current word            |
| `noh`        | Ex   | Remove highlights                               |


## Buffers, Tabs and Windows

| Command        | Mode | Description                        |
| -------------- | ---- | ---------------------------------- |
| `ls`           | Ex   | Print the buffer list              |
| `bn`           | Ex   | Switch to next buffer              |
| `bp`           | Ex   | Switch to previous buffer          |
| `bd`           | Ex   | Delete buffer                      |
| `<C-w>s`       | N    | Split  current window horizontally |
| `<C-w>v`       | N    | Split current window vertically    |
| `<C-w>h/j/k/l` | N    | Move focus                         |
| `<C-w>H/J/K/L` | N    | Move windows                       |
| `<C-w>w`       | N    | Cycle between open windows         |
| `<C-w>c`       | N    | Close active window                |
| `<C-w>o`       | N    | Close all windows except current   |
| `tabnew`       | Ex   | Create a new tab                   |
| `tabclose`     | Ex   | Close a tab                        |
| `gt`           | N    | Switch to next tab                 |


## Files

| Command                      | Mode | Description                  |
| ---------------------------- | ---- | ---------------------------- |
| `w`                          | Ex   | Save file                    |
| `w !sudo tee % > /dev/null/` | Ex   | Save file as root (Vim only) |
| `e`                          | Ex   | Edit file                    |
| `q`                          | Ex   | Exit vim                     |


## Code compilation

| Command             | Mode | Description                           |
| ------------------- | ---- | ------------------------------------- |
| `set makeprg={cmd}` | Ex   | Define the command executed by `make` |
| `make`              | Ex   | Execute command                       |
| `copen`             | Ex   | Open quickfix window                  |
| `cclose`            | Ex   | Close quickfix window                 |
| `cfirst`            | Ex   | Jump to quickfix first item           |
| `clast`             | Ex   | Jump to quickfix last item            |
| `cn`                | Ex   | Jump to next quickfix item            |
| `cp`                | Ex   | Jump to previous quickfix item        |
