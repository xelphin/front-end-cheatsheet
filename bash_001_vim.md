# Vim

> `sudo apt install vim` :   if you don't have it

## Basics

### Open/Close

Open: 
- $`vim`

[In normal mode]

Close: 
- `:q`
    - `:q!` (dismisses any changes you made)

### File

- $`vim <myFile>`
    - opens file or creates it if it doesn't exist

## Modes

When you open a vim file you start out in normal mode.

- INSERT mode
    - `i` (insert mode, insert before curser focus)
        - `[shift]`+`i` (insert at start of line)
    - `a` (insert mode, insert after cursor focus)
        - `[shift]`+`a` (insert at end of line)
    - `o` (insert mode, start typing on new line)
        - `[shift]`+`o` (start typing in new line above cursor focus)
    - `[esc]`  (returns to normal mode)


### Normal Mode

Can use: `h` (left) `j` (down) `k` (up) `l` (right) instead of arrow keys

- `:q`
    - `:q!` (dismisses any changes you made)
- `:w` (writes changes into file)
- `:wq` (write and quit)
- `[number]`+`[action key]` (does action [number] pf times)
    - `5` +`[up arrow]` (goes up 5 lines)

### Insert Mode

Able to write things into file without there being special functionality


## Plugins


#### Show line numbers
`:set number`




