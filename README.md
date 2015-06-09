# Different Vim commands, a cheat sheet

`:h {command}` - help page on the *command*  
[Vim's Wiki](http://vim.wikia.com)

### Content
[Working with files](https://github.com/vicrucann/vimcheat/blob/master/README.md#files)  
[Main commands](https://github.com/vicrucann/vimcheat/blob/master/README.md#commands)  

### Files  

###### Open a file from the current buffer  
`e: path/fname` - open fname  
`e: <Space><C-d>` - list all available directories/files  
`e:` `<Tab><Tab>...` - cycle through all availabe items  

###### Moving between files
`:bn` and `:bp` - move to the next\previous buffer in the list  
`:ls` - list all available buffers   
`:b#` - move between two last used (primary) buffers  
`:bf` and `:bl` - first and last  
`:bm` - next modified  

###### Saving/quitting  
`:w`, `:wq` - write/write-and-close  
`:x` - write buffer if there was a modification  
`:qa!` - quit everything, ignore changes everywhere  
`:wqa` - the opposite  

###### Creating new files  
`:new [fname]` - create empty buffer with horizontal split window  
`:enew [fname]` - within the current buffer  
`:vnew [fname]` - vertical split window  
`:tabnew [fname]` - buffer within new tab  
`:only` - closes all the split windows until there is only one window left open  
`autocmd BufNewFile *.template` # added to .vimrc - new file from template  

###### Switching the working directory  
`:cd ~/new/path` - go to ~/new/path  
`:pwd` - display path to current directory  
`:lcd ~/new/path` - change directory only for current window  

### Commands  
`[count]{operator}{[count]motion|text object}`  

###### Operators  
`yy` - yank the entire line  
`p` and `P` - paste content after\before the current cursor position  
`a` and `i` - insert mode before\after the current position  
`f` and `t` - find spicified characters to the right of current position \ until the specified character  
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

###### Motions  
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
`y` and `Y` - yank (copy) selected text \ copy whole line    
`d` and `dd` - delete selected text \ delete whole line, e.g: `d2w` - delete two words  
`c` - change characters, e.g: `c2w words` - change next to words to "words"  
`gu` - lowercase chars  
`gU` - uppercase chars  

###### Cursor and page movements  
`h` and `l` - one column to the left \ right  
`j` and `k` - one rwo down \ up  
`C-u` and `C-b` - half \ one page up  
`C-d` and `C-g` - half \ one page down  
`C-e` and `C-y` - scroll page down \ up  
`H`, `M` and `L` - move cursor to the top \ middle \ bottom of the viewport  

###### Text objects  
`(i)` - inside   
`(a)` - around  
`(w)` - word, e.g: `viw` - select inside a word, select the whole word no matter where the cursor is within this word  
`(s)` - sentence, e.g: `vis` - select inside sentence  
`(p)` - paragraph, e.g: `vip` - select inside paragraph  
`{}`, `()`, `[]`, `''`, `""` - block and quotations, e.g: `vi"` - select inside quotes, `va{` - select around the brackets  

