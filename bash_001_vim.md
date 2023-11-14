# Vim

> `sudo apt install vim` :   if you don't have it

<details>
<summary>Online Cheatsheets</summary>


Websites:
- https://vim.rtorr.com/
- https://devhints.io/vim

Page:
- https://www.reddit.com/media?url=https%3A%2F%2Fexternal-preview.redd.it%2Fiigrixvxp5aYN9ox7Gr1dfI_rhLRotWlLsCafjJqjEQ.png%3Fauto%3Dwebp%26s%3D1594ddc17408cb9186a73c2a6d1a1bf1e00769dd
</details>


## Basics

### Open/Close

Open: 
- $`vim`

[Now you're in normal mode]

Close: 
- `:q`
    - `:q!` (dismisses any changes you made)
    - `:wq` (writes in the changes you made)

### File

- $`vim <myFile>`
    - opens file or creates it if it doesn't exist

## Modes

When you open a vim file you start out in normal mode.

### Normal Mode

- `[number]`+`[action]` (does action [number] of times)
    - `5` +`[up arrow]` (goes up 5 lines)

#### Moving

- `:set mouse=a` (Makes you be able to move in the file with mouse)
- Can use: `h` (left) `j` (down) `k` (up) `l` (right) instead of arrow keys
- `w` (jump to the next word)
- `b` (jump to previous word)
- `0` (jump to start of line)
- `$` (jump to end of line)
- `%` (if cursor on '`{`' jumps to its '`}`')
- `t`+`<symbol>` (jumps to next symbol (that is on same line))
- `gg` (jump to start of file)
- `G` (jump to end of file)
- `<number>`+`G` (jump to line number)
- `:`+`<number>` (jumps to line number)


#### Change Mode

<details>
<summary>Go to INSERT mode</summary>

Following will put you in Insert Mode:

- `i` (insert mode, insert before curser focus)
    - `[shift]`+`i` (insert at start of line)
- `a` (insert mode, insert after cursor focus)
    - `[shift]`+`a` (insert at end of line)
- `o` (insert mode, start typing on new line)
    - `[shift]`+`o` (start typing in new line above cursor focus)

Go back to Normal Mode:
- `[esc]` 

</details>

<details>
<summary>Go to VISUAL mode</summary>

Following will put you in Visual Mode:
- `v` (visual mode)
- if `:set mouse=a` then can select text

Go back to Normal Mode:
- `[esc]`+`[esc]`  
- `[left mouse click]`

</details>


#### Text Commands

<details>
<summary>Undo/Redo</summary>

- `u` (undo)
- `[ctr]`+`r` (redos)

</details>

<details>
<summary>Delete</summary>

Line:
- `d`+`d` (delete line)
- `D` (delete rest of line)
- `d`+`0` (delete from cursor point till start of line)

Word:
- `d`+`w` (delete following/rest of word)
- `d`+`i`+`w` (delete word currently on)

With Replace:
- `c`+`c` (deletes line and enters insert mode)
    - `C` (delete rest of line and enters insert mode)
    - `c`+`i`+`"` (if inside "here" then can change all inside quotation mark (can do same with `(`, `{`...))
- `r` (replace character currently selected with next character typed)

Special
- `d`+`i`+`"` (if inside "here" delete everything inside the quotation mark (can do same with `(`, `{`...))
-`d`+`%` (if on `{` deletes everything till closing `}`)
-`d`+`t`+`<symbol>` (delete from cursor till symbol (that is on same line))

</details>

<details>
<summary>Copy</summary>

- `y`+`y` (yank/copy line)

Special:    
- `y`+`i`+`"` (if inside "here" yank/copy everything inside the quotation mark (can do same with `(`, `{`...))


</details>

<details>
<summary>Paste</summary>

- `p` (paste (from visual mode yanked/copied text or from commands here))

</details>

#### File

<details>
<summary>quit</summary>

- `:q`
- `:q!` (dismisses any changes you made)
- `:wq` (writes in the changes you made)

</details>

<details>
<summary>save</summary>

- `:w` (writes changes into file)

</details>




### Insert Mode

Able to write things into file without there being special functionality

- `[esc]`  (returns to normal mode)

### Visual Mode

Used for selecting text, use `[arrow keys]` to select your word or your `[mouse drag]`

- `d` (delete)
- `y` (yank/copy)
- `[esc]`+`[esc]`  (returns to normal mode)
- `[left mouse click]` (returns to normal mode)

## Configuration

### Save the configuration

`$ vim ~/.vimrc`

#### How To

Click `i` (to go to insert mode) and then write the following configurations that you want from below (without the '`:`') and then click on `[esc]` and `:wq`.

<details>
<summary>Configurations</summary>


#### Line Numbers
- `:set number` (Show line numbers)
- `:set relativenumber` (Show relative distance from current position)

#### Moving
- `set mouse=a` (Makes you be able to move in the file text during normal mode)

#### Theme
- `:colorscheme <coloscheme>` (can change colorscheme, for example to 'slate', can click [tab] before writing the colorsheme to see options)


</details>







