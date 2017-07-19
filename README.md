# Different Vim commands, a cheat sheet

`:h {command}` - help page on the *command*  
[Vim's Wiki](http://vim.wikia.com)  
Reference: [ProVim](http://link.springer.com/book/10.1007%2F978-1-4842-0250-0)

# Content
[Working with files](https://github.com/vicrucann/vimcheat/blob/master/README.md#files)  
[Main commands](https://github.com/vicrucann/vimcheat/blob/master/README.md#commands)  
[Working with registers](https://github.com/vicrucann/vimcheat/blob/master/README.md#registers)  
[VISUAL-BLOCK mode](https://github.com/vicrucann/vimcheat/blob/master/README.md#visual-block)  
[Navigation, search, replace](https://github.com/vicrucann/vimcheat/blob/master/README.md#navigation-search-and-replace)  
[Makefile](https://github.com/vicrucann/vimcheat/blob/master/README.md#makefile)  
[Buffer, window and tab management](https://github.com/vicrucann/vimcheat/blob/master/README.md#bufferwindowtab-management)  
[Spell check](https://github.com/vicrucann/vimcheat/blob/master/README.md#spell-check)  

# Files  

## Open a file from the current buffer  
`e: path/fname` - open fname  
`e: <Space><C-d>` - list all available directories/files  
`e:` `<Tab><Tab>...` - cycle through all availabe items  

## Moving between files
`:bn` and `:bp` - move to the next\previous buffer in the list  
`:ls` - list all available buffers   
`:b#` - move between two last used (primary) buffers  
`:bf` and `:bl` - first and last  
`:bm` - next modified  

## Saving/quitting  
`:w`, `:wq` - write/write-and-close, e.g: `:w filename` - save as `filename` and continue working on original  
`:w filename` - save as filename and keep working on original  
`:x` - write buffer if there was a modification  
`:qa!` - quit everything, ignore changes everywhere  
`:wqa` - the opposite  
`:sav filename` - save as `filename` and continue working on `filename`  

## Creating new files  
`:new [fname]` - create empty buffer with horizontal split window  
`:enew [fname]` - within the current buffer  
`:vnew [fname]` - vertical split window  
`:tabnew [fname]` - buffer within new tab  
`:only` - closes all the split windows until there ish only one window left open  
`autocmd BufNewFile *.template` # added to .vimrc - new file from template  

## Moving between tabs  
`gt`, `gT` and `{i}gt` - in normal mode, go to next \ previous \ tab in position {i}  
`:tabn` and `:tabp` - go to next \ previous tab  
`C-pgUp` and `C-pgDown` - when in gvim  

## Switching the working directory  
`:cd ~/new/path` - go to ~/new/path  
`:pwd` - display path to current directory  
`:lcd ~/new/path` - change directory only for current window

## `NERDTree` - directory view
`:NERDTree` - open the directory browser in the current window  
`:NERDTreeClose` - close the directory browser in the current window  
`<C>-w-l` - switch the focus from the NERDTree to the file view  
`<C>-w-h` - switch the focus from the file view to the NERDTree  

# Commands  
`[count]{operator}{[count]motion|text object}`  

## Operators  
`yy` - yank the entire line  
`p` and `P` - paste content after\before the current cursor position  
`a` and `i` - insert mode before\after the current position  
`f`/`F` and `t` - find spicified characters to the right of current position \ until the specified character, e.g `f#` - move cursor to the next occurence of `#`  
`;` or `,` - move on the next occurence of chracter defined by `f` or `t`  
`o` and `O` - move cursor to the next \ previous line and enter *INSERT* mode  
`x` - cut the character (selected chars)  
`s` - substitute character (selected chars)  
`S` - substitute entire line  
`u` - undo  
`~` - swap char casing  
`.` - repeat last insert  
`dd` - delete current line  
`D` or `d$` - delete from the cursor to end of line  
`gx` - open url under cursor  

## Motions  
`:h motions`  
`0` and `$` and `g_` - move cursor to the start \ end \ end (exclusive newline) of line  
`b` - move backwards through each word  
`e` - move to the end of the word, e.g: `3e` - end of third word  
`w` - move to the start of the next word, e.g: `3w` - start of fourth word  
`gg` and `G` - start \ end of the buffer, e.g: `5gg` or `5G` - line five  
`%` - next bracket or paranthesis  
`(` and `)` - previous \ next sentence  
`{` and `}` - start and end of a paragraph  
`[(` and `])` - next \ previous available paranthesis  
`[{` and `]}` - next \ previous available bracket  

###### Operators that require motions or other commands  
`v` and `V` - visual mode \ select whole line, e.g: `ve` - select until end of word  
`y` and `yy` - yank (copy) selected text \ copy whole line    
`d` and `dd` - delete selected text \ delete whole line, e.g: `d2w` - delete two words  
`c` - change characters, e.g: `c2w words` - change next to words to "words"  
`gu` - lowercase chars  
`gU` - uppercase chars  

###### Cursor and page movements  
`h` and `l` - one column to the left \ right  
`j` and `k` - one rwo down \ up  
`<C-u>` and `<C-b>` - half \ one page up  
`<C-d>` and `<C-g>` - half \ one page down  
`<C-e>` and `<C-y>` - scroll page down \ up  
`H`, `M` and `L` - move cursor to the top \ middle \ bottom of the viewport  

###### Text objects  
`(i)` - inside   
`(a)` - around  
`(w)` - word, e.g: `viw` - select inside a word, select the whole word no matter where the cursor is within this word  
`(s)` - sentence, e.g: `vis` - select inside sentence  
`(p)` - paragraph, e.g: `vip` - select inside paragraph  
`{}`, `()`, `[]`, `''`, `""` - block and quotations, e.g: `vi"` - select inside quotes, `va{` - select around the brackets  

###### Insert mode commands  
`:h ins-special-special` - documentation  
`<C-o>` - mode to run commands in insert mode  

### Registers  
`""` - unnamed register, used after commands delete `d`, change `c`, substitute `s`, cut `x`, yank `y`; also it is used as *last used register*, e.g: `""p` - paste from unnamed register  
`"0... "9` - numbered, used with commands yank `y` and delete `d`, e.g: `viw"2y` - copy whole word to specified register *2*; `"2p` - paste from specified register *2*   
`"a... "z` or `"A... "Z` - named (small case overwrite, capital case - appends to the current buffer), e.g: `"ay` copy to register *a*, `"Ay` - append to register *a*  
`":`, `".`, `"%` and `"#` - read only: most recently executed command \ for last edit made via *insert* mode \ name of the current file \ name of the alternative file   
`"=` - expression  
`"/` - last search pattern
`:reg` - view content of the registers, e.g: `:reg 0 * a`  

### Visual block 
`C-v` - enter into VISUAL-BLOCK mode  
`C-c` - keep the changes made to the current line but not apply them automatically to other lines  
`Esc` - move back to NORMAL mode (and apply the changes to the rest lines of the selection of VISUAL-BLOCK mode)  

### Navigation, search and replace 
`[count]gg` or `[count]G` - move cursor to line `count`  
`f` and `F` - search forward and backward, e.g: `f#` - search `#` character
`;` and ',' - move your cursor onto next occurence of the character you tried to match with `f` and `F`  
`/` - using in regex search command, e.g: `/function` - finds all occurences of word `function`  
`n` and `N` - navigates throughout the search results from `/` operator  
`%` - detects a block (bracket) and moves to a closing one  
`vt{x}` and `va{x}` - select until and select around the block, e.g: `va{`, `va[t)` - select around `[` and til `)`  
`:s/{pattern}/{replacement}/{flags}` - find and replace, e.g: `:%s/foo/bar/gc` - Change each `foo` to `bar`, but ask for confirmation first (flag `g` stands for global and `c` - confirmation first)  
  
`:find foo.txt` or `:sfind foo.txt` - search specific file or open it in a split window  
`/searchword` or `?searchword` - highlight "searchword"  
`n` or `N` - to navigate through each match  
`*` or `#` - search forward or backward for word where the cursor is

### Makefile  
`:map <f9> :make` - vimrc, map the <F9> to run make  
`:set makeprg` - change what `:make` does  
`:copen` - open a mini-window with list of errors; hit enter on an error to jump to line  
`:cclose` - closes the mini-window  
`:cw` - toggles the mini-window (if errors exist)  
`:cn` - goto the next error in source code  
`:cp` - goto the previous error in source code  
`:cfirst` - goto the first error in source code  
`:clast` - goto the last error in source code  
`map cn <esc>:cn<cr>` - in vimrc to map `:cn` command  
`map cp <esc>:cp<cr>` - in vimrc to map `:cp` command  

### Buffer/window/tab management 
`:ls` - list all currently open buffers  
`:sba` or `:vert sba` - split all the open windows into horizontal / vertical windows  
`:bd *.ext` - "buffer delete": close all windows with `.ext` extension  
`:bd 1 3 5` - buffer delete and number(-s)
`:4,7 bd` - buffer delete using range  
`:bufdo bd` - close all at once  
`:sp [file]` or `:vs [file]` - create horizontal/vertical window split (and opens [filename] in there)  
`:on` or `:only` - close all but current one  
`<C-w>H` or `<C-w>J` or `<C-w>K` or `<C-w>L` - left/down/up/right - changing the window layout  
`:resize +{n}` or `:resize -{n}` - increase / reduce the window height by `{n}` amount  
`:vertical resize +{n}` or `:vertical resize -{n}` - same as above but for width  
`<C-w>_` - maximize the window height  
`<C-w>|` - maximize the window width  
`<C-w>=` - resize all windows to balanced dimensions  
`<C-w>T` - move current window into its own tab  
`:tabnew` - create new tab  
`gt` and `gT` - move between the tabs  
`:tabonly` - close all but current tab  
`:tabmove 1` - rearrange tabs   

### Plugins
`:NERDTree` - open file manager  
* `<C-w> <left>` or `<C-w> <right>` - move between file manager and main vim window
* `r` - updates the current folder content on NERDTree

### Spell check
`:set spell spelllang=en_us` - turn the spell on with specified language (US English)  
`:setlocal spell spelllang=en_us` - use it only for local buffer  
`:set nospell` - turn the spell off  
`[s` and `]s` - move between the misspelled words  
`z=` - once the curson is on the word, the command will provide a list of possible corrections  
`zg` - add the word to dictionary  
`zw` - mark the word as incorrect  
`set spell spelllang=en_us` - add to vimrc to remember the language setting  
